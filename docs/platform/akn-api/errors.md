---
sidebar_position: 8
title: Errors
---

# Errors

Four error shapes are in use, and one group of endpoints reports failure inside
a 200 response. A caller must handle all five.

## Shapes

| Shape | Body | Used by |
|-------|------|---------|
| General | `{"error":"<message>"}` | Sessions, people, notifications, calendar, status |
| Qualified | `{"error":"<message>","reason":"<value>"}` | Approval and account status refusals |
| OAuth | `{"error":"<code>"}`, sometimes with `error_description` | The `/auth/oidc` endpoints |
| HTML page | A rendered page, not JSON | `/auth/bridge` errors, and the OIDC callback refusal |
| Success-shaped | 200 with a false flag in the body | `POST /auth/verify`, `/location`, `/calendar` |

The `error` message is intended for a developer. It is not stable and must not
be matched on. Branch on the status code, and on `reason` where one is present.

## Status codes

| Status | Meaning | Retry |
|--------|---------|-------|
| 200 | Handled. Check the body before assuming success | Not applicable |
| 204 | Preflight answered | Not applicable |
| 302 | Redirect in a browser flow | Follow it |
| 400 | Request is malformed, or a required field is missing | Only after correcting the request |
| 401 | Credential absent, invalid or expired | After obtaining a new credential |
| 403 | Credential is valid, the account may not do this | No. Escalate to an administrator |
| 404 | No such record, or no such provider | No |
| 409 | The change conflicts with an existing link | No. Resolve the conflict first |
| 429 | Rate limit reached on an email code endpoint | After the interval stated in the message |
| 500 | The request failed inside the service or an upstream | Once, then escalate |
| 502 | An upstream returned an unusable answer | Once, then escalate |
| 503 | A dependency is unavailable, or a provider is disabled | Yes, with backoff |

## Distinguishing 401 from 403

| Status | Interpretation | Correct handling |
|--------|----------------|------------------|
| 401 | The service does not know who is calling | Sign in again |
| 403 | The service knows, and refuses | Do not retry. Do not sign the person out |
| 503 with `Authorization unavailable` | The account could not be looked up | Retry. Do not sign the person out |

A caller that treats every refusal as a sign-in failure loops a person through
sign-in indefinitely when their account is `pending`.

## Approval refusals

`POST /auth/verify` answers 200 when the token is valid and the account is not
permitted.

| `reason` | Meaning |
|----------|---------|
| `pending` | The account exists and has not been reviewed |
| `rejected` | The account has been refused |
| `no_project_access` | Approved, but without a grant for the requested project |
| `phone_not_linked` | Returned with 403. The number is on no account |

Gated endpoints answer 403 with the same vocabulary in `reason`.

## OAuth error codes

| Code | Cause |
|------|-------|
| `invalid_client` | The client is not registered, or the secret does not match |
| `invalid_request` | A required parameter is missing, or the redirect URI is not registered |
| `unsupported_response_type` | Anything other than `code` |
| `unsupported_grant_type` | Anything other than `authorization_code` |
| `invalid_grant` | The code is unknown, expired, already used, bound to another client, or the redirect URI or PKCE verifier does not match |
| `invalid_token` | The access token is unknown or expired |
| `server_error` | Token signing failed |

An invalid authorise request is answered to the caller. It is never delivered to
the requested redirect URI.

## Non-JSON errors

The bridge endpoints and the OIDC callback refusal render HTML. A client that
sets `Accept: application/json` still receives HTML. Check the content type
before parsing, or branch on the status code alone.

## Silent failures

| Endpoint | Failure presentation |
|----------|---------------------|
| `GET /calendar/events` | `{"events":[]}` with 200, whether the week is empty or the calendar is unreachable |
| `GET /calendar/upcoming-locations` | `{"locations":[]}` with 200 |
| Every `/location` endpoint | 200 with a fallback body. See [Location](location.md) |
| `PATCH /auth/people/:personId` | 200 with failures listed in `firebaseSyncErrors` |
| `POST /auth/otp/send` for an unknown address | `{"ok":true}` with 200, and no mail sent |
| `POST /auth/zitadel/claims` when the lookup fails | 200 with the `urn:akn:` claims absent |

None of these raise a status code a caller can trap. Inspect the body.

## Cross-origin failures

A browser request from an origin outside the allowlist receives no allow-origin
header, so the browser rejects the response before the caller sees it. This
presents as a network error, not as a 401 or 403. The request itself reached the
service and may have taken effect.

## Related

- [Authentication](authentication.md) covers the allowlist and rate limits.
- [Diagnostics](diagnostics.md) maps conditions to resolutions.
