---
sidebar_position: 2
title: Authentication
---

# Authentication

Six credential types are accepted. Which one an endpoint takes is fixed per
endpoint and is listed on the reference page for that group.

## Credential types

| Credential | Presented as | Accepted by |
|------------|--------------|-------------|
| Session cookie | `Cookie: __session=<value>` | Session, people, status and project-gated endpoints |
| ID token | `Authorization: Bearer <id_token>` | `POST /auth/verify` in the body, and project-gated endpoints in the header |
| API key | `x-api-key: <key>` | `POST /startpage/notify` |
| OIDC access token | `Authorization: Bearer <access_token>` | `GET /auth/oidc/userinfo` |
| OIDC client credentials | Basic authorisation, or `client_id` and `client_secret` in the body | `POST /auth/oidc/token` |
| Request signature | `ZITADEL-Signature: t=<unix>,v1=<hex>` | `POST /auth/zitadel/claims` |

Public endpoints accept no credential and ignore any that is sent.

## Obtaining a credential

| Credential | How it is obtained |
|------------|--------------------|
| ID token | Sign in at https://id.akn.me.uk. The sign-in produces an ID token for the account |
| Session cookie | Exchange an ID token at `POST /auth/verify`. The response sets the cookie |
| Custom token | `POST /auth/otp/sign-in` and the bridge callback both return a custom token, which the browser exchanges for an ID token |
| API key | Issued by the site operator. There is no self-service path |
| OIDC client credentials | Registered by the site operator against a fixed redirect URI allowlist |
| Signing secret | Shared with the upstream identity provider by the site operator |

## Sessions

`POST /auth/verify` sets the session cookie on a successful, approved sign-in.

| Property | Value |
|----------|-------|
| Name | `__session` |
| Lifetime | 14 days from issue |
| Domain | `.akn.me.uk`, so every akn subdomain sends it |
| Flags | `HttpOnly`, `Secure`, `SameSite=Lax` |
| Renewal | None. A new cookie requires a fresh call to `POST /auth/verify` |
| Revocation | `POST /auth/logout` clears the cookie in the calling browser only |

Two cookie formats verify successfully: the current akn ID session token and the
older provider session cookie issued before the cutover. A caller does not
choose which is issued.

`POST /auth/session/refresh` reports whether the cookie is still valid and
returns the person behind it. It does not extend the lifetime.

## Authorisation

Authentication proves the account. Three further checks decide access.

| Check | Applies to | Requirement |
|-------|-----------|-------------|
| Account status | Every gated endpoint | The person's status is `approved` |
| Project grant | Project-gated endpoints | `projects` contains the required name or `*`, or the role is `admin` |
| Admin role | People administration | The role is `admin` |

The status values a caller can encounter are `pending`, `approved` and
`rejected`. A person who has never been reviewed is `pending`.

| Project name | Gates |
|--------------|-------|
| `startpage` | `GET /startpage/notifications`, `GET /calendar/events` |
| `status` | The `/status` endpoints, alongside the admin role |

## Refused requests

| Condition | Status | Body |
|-----------|--------|------|
| No credential, or one that does not verify | 401 | `{"error":"Unauthorized"}` |
| Verified account with no person record | 403 | `{"error":"Forbidden"}` |
| Verified account not approved | 403 | `{"error":"Forbidden","reason":"pending"}` |
| Approved account without the project grant | 403 | `{"error":"Forbidden"}` |
| Approved account without the admin role | 403 | `{"error":"Forbidden"}` |
| Account lookup unavailable | 503 | `{"error":"Authorization unavailable"}` |

A 503 is not an authentication failure. Retry rather than discarding the
credential and signing in again.

`POST /auth/verify` is the exception to the table. A sign-in that authenticates
but is not approved returns 200 with `approved: false` and a reason. See
[Sessions and sign-in](sessions.md).

## Cross-origin requests

| Caller origin | Behaviour |
|---------------|-----------|
| `https://akn.me.uk`, `https://www.akn.me.uk`, `https://id.akn.me.uk`, `https://halcyon.akn.me.uk`, `https://startpage.akn.me.uk`, `https://thoughts.akn.me.uk`, `https://status.akn.me.uk` | Allowed, with credentials |
| Any origin, on `/auth/oidc/` paths and the root discovery document | Allowed, without credentials |
| Any other origin | No allow-origin header is returned. The browser blocks the response |

| Property | Value |
|----------|-------|
| Methods | `GET`, `POST`, `PATCH`, `DELETE`, `OPTIONS` |
| Request headers | `Content-Type`, `Authorization`, `x-api-key` |
| Preflight | `OPTIONS` answers 204 |
| Credentialed requests | Send the session cookie only from an allowed origin |

A caller on an origin outside the list works server to server, where the browser
policy does not apply.

## Rate limits

| Surface | Limit |
|---------|-------|
| `POST /auth/otp/send` | One code per address per 60 seconds, and five per address per hour |
| Email code attempts | Five attempts per code, after which the code is destroyed |
| Every other endpoint | No limit is applied |

## Related

- [Sessions and sign-in](sessions.md) covers the endpoints that issue and end sessions.
- [Errors](errors.md) covers status codes and error bodies in full.
- [Diagnostics](diagnostics.md) covers refused credentials and blocked origins.
