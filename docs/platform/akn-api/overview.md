---
sidebar_position: 1
title: Overview
---

# aknAPI

| | |
|---|---|
| URL | https://api.akn.me.uk |
| Description | HTTP API for akn ID sessions, federated sign-in, and the data served to akn's own sites |
| Access | Public endpoints are open. The rest require an approved akn ID account, a project grant, an API key, or a registered OIDC client |
| Pricing | Free |

## Overview

aknAPI allows a developer to verify an akn ID sign-in, open and refresh a
session, and read the status, role and project grants attached to the person
behind it. Authorisation controls are held by akn ID: every gated endpoint
checks account status first, then the project grant the endpoint requires.

The same service acts as an OpenID Connect provider for relying parties, bridges
sign-in methods that cannot be used directly, and serves the notification,
calendar, status and location data behind akn's own sites.

## Capabilities

| Capability | Availability |
|------------|--------------|
| Verify a sign-in and open a session | Any caller holding a valid ID token |
| Read the signed-in person's status, role and project grants | Session cookie or bearer ID token |
| Sign in with a code sent to an email address | Public |
| Request an account | Public |
| Sign in through a bridged provider | Public |
| Act as an OpenID Connect provider, authorisation code flow | Registered relying parties |
| Supply authorisation claims to an upstream identity provider | Signed callers only |
| Administer people, grants and linked identities | Admin role |
| Submit a notification | API key holders |
| Read notifications and the owner's calendar | `startpage` project grant |
| Read location and visitor summaries | Public |
| Manage status incidents and monitored URLs | Admin role, or `status` project grant |
| Refresh tokens on the OIDC provider | Not available |
| Dynamic client registration | Not available |
| Single logout across relying parties | Not available |
| Pagination on any list endpoint | Not available |
| Webhooks or streaming responses | Not available |
| Deleting a person | Not available |
| Rate limiting outside the email code endpoints | Not available |

## Endpoint groups

| Group | Path prefix | Purpose |
|-------|-------------|---------|
| Sessions and sign-in | `/auth` | Verify a sign-in, hold a session, obtain a credential |
| People administration | `/auth/people`, `/auth/sync` | Manage people, grants and linked identities |
| OpenID Connect | `/auth/oidc`, `/auth/zitadel` | Federate akn ID to a relying party or an upstream provider |
| Notifications, calendar and status | `/startpage`, `/calendar`, `/status` | Data for the startpage and status sites |
| Location | `/location` | Location summaries and visitor records |

## Service check

`GET /` requires no credential and answers with a fixed body.

```json
{ "ok": true, "service": "akn-api" }
```

## Conventions

| Property | Detail |
|----------|--------|
| Request bodies | JSON. The token endpoint also accepts form encoding |
| Response bodies | JSON, except bridge errors, which are HTML pages |
| Timestamps | ISO 8601 in UTC, unless stated otherwise on the endpoint |
| Versioning | None. Paths are unversioned and change in place |
| Idempotency | Not offered. No request identifier is honoured |

## Next steps

- [Authentication](authentication.md) covers credentials, sessions and CORS.
- [Sessions and sign-in](sessions.md) covers the session and credential endpoints.
- [Errors](errors.md) covers the error shapes a caller must handle.
- [Diagnostics](diagnostics.md) lists integration conditions and resolutions.

## Related products

- [aknID](../../platform/akn-id/overview.md), sign-in provider for sessions this API issues
