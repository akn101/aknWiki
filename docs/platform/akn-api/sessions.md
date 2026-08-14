---
sidebar_position: 3
title: Sessions and sign-in
---

# Sessions and sign-in

Endpoints that turn a sign-in into a session, report on that session, end it,
and produce a credential for methods that cannot sign in directly.

| Method | Path | Credential |
|--------|------|-----------|
| POST | `/auth/verify` | ID token in the body |
| POST | `/auth/session/refresh` | Session cookie |
| POST | `/auth/logout` | None |
| POST | `/auth/project-access` | Session cookie |
| POST | `/auth/exchange` | Single-use code in the body |
| POST | `/auth/otp/send` | None |
| POST | `/auth/otp/verify` | None |
| POST | `/auth/otp/sign-in` | None |
| GET | `/auth/bridge/` | None |
| GET | `/auth/bridge/:provider/start` | None |
| GET | `/auth/bridge/:provider/callback` | State cookie set at start |

## POST /auth/verify

Verifies an ID token, resolves the person behind it, checks approval and the
project grant, and sets the session cookie.

Request body.

| Field | Type | Required | Detail |
|-------|------|----------|--------|
| `idToken` | string | Yes | ID token from akn ID sign-in |
| `project` | string | Yes | Project the caller is gating on |

Approved response, 200. The session cookie is set on this response.

```json
{
  "approved": true,
  "uid": "…",
  "personId": "…",
  "email": "person@example.com",
  "name": "…",
  "role": "user",
  "projects": ["startpage"],
  "groups": []
}
```

Refused responses.

| Condition | Status | Body |
|-----------|--------|------|
| Account not approved | 200 | `{"approved":false,"reason":"pending"}` |
| Approved, no grant for `project` | 200 | `{"approved":false,"reason":"no_project_access"}` |
| A field is missing | 400 | `{"error":"idToken and project required"}` |
| Sign-in proved a phone number only, and that number is on no account | 403 | `{"approved":false,"reason":"phone_not_linked","error":"…"}` |
| Token does not verify | 401 | `{"error":"Invalid token"}` |

A 200 with `approved: false` sets no cookie. Test the field, not the status
code.

The first successful verification for an unrecognised sign-in creates a person
record with status `pending`. Phone is the exception: it resolves an account
that already carries the number and refuses otherwise.

## POST /auth/session/refresh

Reports whether the session cookie is still valid, and returns the person behind
it. Takes no body.

Response, 200.

```json
{
  "authenticated": true,
  "uid": "…",
  "personId": "…",
  "email": "person@example.com",
  "name": "…",
  "role": "user",
  "projects": ["startpage"],
  "groups": []
}
```

An `X-Remote-User` response header carries the email address when one is known.

| Condition | Status | Body |
|-----------|--------|------|
| No cookie, or the cookie does not verify | 401 | `{"authenticated":false}` |

The cookie lifetime is unchanged by this call.

## POST /auth/logout

Clears the session cookie. Takes no body and no credential. Always answers 200
with `{"ok":true}`.

The cookie is cleared in the calling browser. Sessions held elsewhere continue
until they expire.

## POST /auth/project-access

Records that the signed-in person reached a project.

| Field | Type | Required |
|-------|------|----------|
| `project` | string | Yes |

| Condition | Status | Body |
|-----------|--------|------|
| Recorded | 200 | `{"ok":true}` |
| Cookie or `project` missing | 400 | `{"error":"missing params"}` |
| Cookie does not verify | 401 | `{"error":"Unauthorized"}` |

## POST /auth/exchange

Redeems a single-use code for the person it was issued to. The code is consumed
whether or not the person turns out to be approved.

| Field | Type | Required |
|-------|------|----------|
| `code` | string | Yes |

Response, 200.

```json
{
  "uid": "…",
  "personId": "…",
  "email": "person@example.com",
  "name": "…",
  "role": "user",
  "projects": ["startpage"]
}
```

| Condition | Status | Body |
|-----------|--------|------|
| `code` missing | 400 | `{"error":"code required"}` |
| Code unknown | 401 | `{"error":"Invalid code"}` |
| Code already redeemed | 401 | `{"error":"Code already used"}` |
| Code past its expiry | 401 | `{"error":"Code expired"}` |
| Code resolves to nothing | 401 | `{"error":"User not found"}` or `{"error":"Person not found"}` |
| Person not approved | 403 | `{"error":"Account not approved","reason":"pending"}` |

## Email codes

Three endpoints implement sign-in by a six-digit code sent to an email address.
The `purpose` field selects between them.

| Purpose | Meaning |
|---------|---------|
| `signin` | Default. An existing person proves control of an address already on their record |
| `request-access` | A stranger proves an address is real so an account request can be reviewed |

| Property | Value |
|----------|-------|
| Code format | Six digits |
| Lifetime | 10 minutes |
| Attempts | Five per code, after which the code is destroyed |
| Reuse | Single use. Sign-in consumes it |
| Resend | One code per address per 60 seconds |
| Volume | Five codes per address per hour |

### POST /auth/otp/send

| Field | Type | Required | Detail |
|-------|------|----------|--------|
| `email` | string | Yes | Address to send to |
| `purpose` | string | No | `signin` or `request-access`. Defaults to `signin` |

| Condition | Status | Body |
|-----------|--------|------|
| Sent | 200 | `{"ok":true}` |
| `purpose` is `signin` and no account holds the address | 200 | `{"ok":true}` |
| Address is malformed | 400 | `{"error":"A valid email is required"}` |
| Resent inside 60 seconds | 429 | `{"error":"A code was just sent. Please wait a minute."}` |
| Hourly limit reached | 429 | `{"error":"Too many codes requested. Try again later."}` |
| Mail delivery not configured | 503 | `{"error":"Email is not configured"}` |
| Delivery failed | 500 | `{"error":"Could not send a code"}` |

A sign-in request for an address with no account is answered identically to a
successful send. A caller cannot use this endpoint to test whether an address
has an account.

### POST /auth/otp/verify

Checks a code without consuming it.

| Field | Type | Required |
|-------|------|----------|
| `email` | string | Yes |
| `otp` | string | Yes |
| `purpose` | string | No |

| Condition | Status | Body |
|-----------|--------|------|
| Code correct | 200 | `{"valid":true}` |
| Code wrong, or the purpose does not match | 400 | `{"valid":false,"error":"Invalid code"}` |
| Code expired | 400 | `{"valid":false,"error":"That code expired. Request a new one."}` |
| Attempt limit reached | 400 | `{"valid":false,"error":"Too many attempts. Request a new code."}` |

A wrong code consumes an attempt. An expired code or an exhausted attempt count
destroys the code.

### POST /auth/otp/sign-in

Consumes the code and returns a custom token for the browser to exchange for an
ID token. The purpose is always `signin`.

| Field | Type | Required |
|-------|------|----------|
| `email` | string | Yes |
| `otp` | string | Yes |

| Condition | Status | Body |
|-----------|--------|------|
| Signed in | 200 | `{"customToken":"…"}` |
| Code wrong, expired or exhausted | 400 | `{"error":"…"}` |
| Address holds no account | 403 | `{"error":"No account for that address"}` |
| Account not approved | 403 | `{"error":"Your account is pending"}` |
| Sign-in failed | 500 | `{"error":"Sign-in failed"}` |

Exchange the custom token for an ID token, then call `POST /auth/verify` to open
a session.

## Bridged providers

A bridge carries a sign-in method that cannot be used directly, and finishes by
handing a custom token to https://id.akn.me.uk.

| Provider | Identifier | State |
|----------|-----------|-------|
| akn ID, and the providers behind it | `zitadel` | Available when configured. Select one with the `idp` parameter |
| Steam | `steam` | Available |
| Instagram | `instagram` | Not available. Registered and permanently disabled |

Accepted `idp` values on the `zitadel` bridge are `google`, `linkedin`,
`github`, `apple` and `aknid`. The browser is sent straight to the provider.

### GET /auth/bridge/

Lists the bridges that are usable. Disabled bridges are omitted.

```json
{ "providers": [ { "id": "steam", "label": "Steam", "start": "/auth/bridge/steam/start" } ] }
```

### GET /auth/bridge/:provider/start

| Parameter | In | Required | Detail |
|-----------|----|----------|--------|
| `provider` | Path | Yes | Identifier from the table above |
| `redirect` | Query | No | Where to send the browser afterwards. Defaults to `https://id.akn.me.uk/account` |
| `idp` | Query | No | Provider to select on the `zitadel` bridge |

Answers 302 to the provider. A state cookie scoped to `/auth/bridge` is set and
is valid for 10 minutes.

`redirect` must be `https` on one of the akn hostnames. Any other destination is
refused.

### GET /auth/bridge/:provider/callback

Called by the provider. Verifies the assertion, resolves or creates the person,
and answers 302 to `https://id.akn.me.uk/` carrying `customToken` and
`redirect` query parameters.

| Condition | Status | Response |
|-----------|--------|----------|
| Unknown provider | 404 | HTML page |
| Provider disabled | 503 | HTML page |
| `redirect` not allowed | 400 | HTML page |
| State missing, altered or older than 10 minutes | 400 | HTML page |
| Provider did not confirm the sign-in | 401 | HTML page |
| Provider returned no stable account identifier | 502 | HTML page |
| Anything else | 500 | HTML page |

Bridge errors are HTML, not JSON. A caller parsing the response as JSON fails on
every error path.

A bridged sign-in that matches no existing person creates one with status
`pending`. It never self-approves.

## Related

- [Authentication](authentication.md) covers credential types and the cookie.
- [People administration](people.md) covers approving an account.
- [Errors](errors.md) covers the shapes above in full.
