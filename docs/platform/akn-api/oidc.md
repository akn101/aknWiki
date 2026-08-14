---
sidebar_position: 5
title: OpenID Connect
---

# OpenID Connect

aknAPI acts as an OpenID Connect provider for registered relying parties, and as
a claims source for the upstream identity provider that fronts akn ID.

| Property | Value |
|----------|-------|
| Issuer | `https://api.akn.me.uk` |
| Flow | Authorisation code |
| Signing algorithm | RS256 |
| Client authentication | `client_secret_post` and `client_secret_basic` |
| PKCE | `S256` and `plain` |
| Scopes advertised | `openid`, `email`, `profile` |
| Subject type | `public` |
| Refresh tokens | Not available |
| Dynamic client registration | Not available |
| End-session endpoint | Not available |

Clients are registered by the site operator against a fixed redirect URI
allowlist. A client may also carry a required project, in which case only people
holding that grant, the `*` grant, or the admin role receive a code.

## Endpoints

| Method | Path | Credential |
|--------|------|-----------|
| GET | `/.well-known/openid-configuration` | None |
| GET | `/auth/oidc/.well-known/openid-configuration` | None |
| GET | `/auth/oidc/jwks` | None |
| GET | `/auth/oidc/authorize` | None. The browser is redirected to sign in |
| GET | `/auth/oidc/callback` | Session cookie. Called by the sign-in page |
| POST | `/auth/oidc/token` | Client credentials |
| GET | `/auth/oidc/userinfo` | Access token |

Discovery is served at both paths with identical content. A client that asserts
the issuer matches the discovery host should use the root path.

## GET /auth/oidc/authorize

| Parameter | Required | Detail |
|-----------|----------|--------|
| `response_type` | Yes | Must be `code` |
| `client_id` | Yes | Registered client |
| `redirect_uri` | Yes | Must match the client's allowlist exactly |
| `state` | No | Returned on the redirect back |
| `nonce` | No | Copied into the ID token |
| `code_challenge` | No | PKCE challenge |
| `code_challenge_method` | No | `S256` or `plain` |

A valid request answers 302 to https://id.akn.me.uk to sign in, and the browser
returns to `/auth/oidc/callback`.

| Condition | Status | Body |
|-----------|--------|------|
| `response_type` is not `code` | 400 | `{"error":"unsupported_response_type"}` |
| Client not registered | 401 | `{"error":"invalid_client"}` |
| `redirect_uri` missing | 400 | `{"error":"invalid_request","error_description":"redirect_uri required"}` |
| `redirect_uri` not on the allowlist | 400 | `{"error":"invalid_request","error_description":"redirect_uri not registered"}` |

Errors are returned to the caller, never delivered to the requested
`redirect_uri`. A relying party that only inspects its callback sees nothing at
all when a request is rejected here.

The pending request expires five minutes after `/auth/oidc/authorize` is called.
A sign-in that takes longer returns `Login session expired. Please try again.`
as plain text with status 400.

## GET /auth/oidc/callback

Called with the state issued at `/auth/oidc/authorize` once the session cookie
is set. Issues the authorisation code and answers 302 to the relying party's
`redirect_uri` with `code`, and `state` when one was supplied.

| Condition | Result |
|-----------|--------|
| No valid session | 302 back to the sign-in page |
| Signed in without the client's required project | 403 with an HTML page naming the missing project |
| Signed in and permitted | 302 to `redirect_uri` |

An unauthorised person is not redirected to the relying party. The refusal is
shown on this page.

## POST /auth/oidc/token

Accepts `application/x-www-form-urlencoded` or JSON.

| Field | Required | Detail |
|-------|----------|--------|
| `grant_type` | Yes | Must be `authorization_code` |
| `code` | Yes | Code from the callback redirect |
| `redirect_uri` | Yes | Must equal the value used at `/auth/oidc/authorize` |
| `client_id` | Conditional | Omit when using Basic authorisation |
| `client_secret` | Conditional | Omit when using Basic authorisation |
| `code_verifier` | Conditional | Required when a challenge was sent and the client has a registered allowlist |

Response, 200.

```json
{
  "access_token": "…",
  "token_type": "Bearer",
  "expires_in": 3600,
  "id_token": "…"
}
```

| Condition | Status | Body |
|-----------|--------|------|
| Client unknown, or the secret does not match | 401 | `{"error":"invalid_client"}` |
| `grant_type` is not `authorization_code` | 400 | `{"error":"unsupported_grant_type"}` |
| Code unknown, already redeemed, or older than two minutes | 400 | `{"error":"invalid_grant"}` |
| `redirect_uri` differs from the authorise request | 400 | `{"error":"invalid_grant"}` |
| Code redeemed by a different client | 400 | `{"error":"invalid_grant"}` |
| PKCE verifier missing | 400 | `{"error":"invalid_grant","error_description":"code_verifier required"}` |
| PKCE verifier does not match | 400 | `{"error":"invalid_grant","error_description":"PKCE verification failed"}` |
| Signing failed | 500 | `{"error":"server_error"}` |

## ID token claims

| Claim | Detail |
|-------|--------|
| `iss` | `https://api.akn.me.uk` |
| `aud` | The client id |
| `sub` | Sign-in identity of the person |
| `email` | Address on the session, or on the person record |
| `email_verified` | True only when the address was proved |
| `phone_number` | Present only when a number is held |
| `phone_number_verified` | Present alongside `phone_number` |
| `name` | Display name, falling back to the address |
| `akn_role` | `user` or `admin` |
| `akn_projects` | Array of project grants |
| `nonce` | Present when supplied at the authorise request |

`email_verified` reflects the real state. Do not key an account on `email` alone
when the claim is false.

## GET /auth/oidc/userinfo

Requires `Authorization: Bearer <access_token>`.

```json
{
  "sub": "…",
  "email": "person@example.com",
  "email_verified": true,
  "name": "…",
  "akn_role": "user",
  "akn_projects": ["startpage"]
}
```

| Condition | Status | Body |
|-----------|--------|------|
| No bearer header | 401 | `{"error":"invalid_token"}` with `WWW-Authenticate: Bearer` |
| Token unknown or older than one hour | 401 | `{"error":"invalid_token"}` |

## Lifetimes

| Item | Lifetime | Reuse |
|------|----------|-------|
| Pending authorise request | 5 minutes | Single use |
| Authorisation code | 2 minutes | Single use |
| Access token | 1 hour | Reusable until expiry |
| ID token | 1 hour | Not accepted back by this service |

Pending requests, codes and access tokens are held for the life of the process.
A restart invalidates every one of them: sign-ins in flight fail, and calls to
`/auth/oidc/userinfo` with a previously valid token answer 401. ID tokens
already issued remain valid until they expire, since they are verified against
the published key.

## Claims target

`POST /auth/zitadel/claims` supplies akn ID authorisation to the upstream
identity provider while it mints a token. It is not a general-purpose endpoint.

| Property | Detail |
|----------|--------|
| Credential | `ZITADEL-Signature: t=<unix>,v1=<hex>` over the exact request body |
| Replay window | 300 seconds either side of the timestamp |
| Refused | 403 with `{"error":"invalid_signature"}` |

Response, 200.

```json
{
  "append_claims": [ { "key": "urn:akn:role", "value": "user" } ],
  "append_log_claims": ["akn: matched person … on email"]
}
```

| Claim | Detail |
|-------|--------|
| `email`, `email_verified` | Appended when the caller proved a verified address |
| `phone_number`, `phone_number_verified` | Appended when a verified number was proved |
| `urn:akn:person_id` | The person the identifiers resolved to |
| `urn:akn:status` | `pending`, `approved` or `rejected` |
| `urn:akn:role` | `user` or `admin` |
| `urn:akn:projects` | Array of project grants |

A signed call that resolves no person still answers 200, with the `urn:akn:`
claims absent. A relying party must treat a missing `urn:akn:projects` as no
access rather than as an error, because a lookup failure produces the same
result.

## Related

- [Authentication](authentication.md) covers the session that `/auth/oidc/callback` reads.
- [Errors](errors.md) covers the difference between OAuth error codes and the rest of the API.
- [Diagnostics](diagnostics.md) covers failed relying party integrations.
