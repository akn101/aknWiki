---
sidebar_position: 4
title: People administration
---

# People administration

Endpoints for managing people, their grants, and the sign-in identities linked
to them. Every endpoint on this page requires a session cookie belonging to a
person whose role is `admin`. A bearer ID token is not accepted here.

| Method | Path | Purpose |
|--------|------|---------|
| GET | `/auth/people` | List people |
| GET | `/auth/people/:personId` | Read one person with identities and identifiers |
| POST | `/auth/people` | Create a person |
| PATCH | `/auth/people/:personId` | Update a person |
| POST | `/auth/people/:personId/link` | Link a sign-in identity to a person |
| DELETE | `/auth/people/:personId/identity/:uid` | Unlink a sign-in identity |
| POST | `/auth/sync/firebase` | Reconcile sign-in accounts against people |
| POST | `/auth/sync/carddav` | Import contacts into people |
| POST | `/auth/provision` | Update a person by sign-in identity. Retained for compatibility |

## The person record

| Field | Type | Detail |
|-------|------|--------|
| `personId` | string | Stable identifier for the person |
| `name` | string | Display name |
| `email` | string or null | Primary address |
| `avatar` | string or null | Image URL |
| `status` | string | `pending`, `approved` or `rejected` |
| `role` | string | `user` or `admin` |
| `projects` | array | Project grants. `*` grants every project |
| `groups` | array | Group names |
| `tags` | array | Free-form labels |
| `createdAt` | timestamp | Set on creation |
| `lastSeen` | timestamp | Updated by a successful `POST /auth/verify` |

A person is distinct from a sign-in identity. One person holds many identities,
one per method they have signed in with. Access is decided on the person.

## GET /auth/people

Returns the 200 most recently created people, newest first.

```json
{ "people": [ { "personId": "…", "name": "…", "status": "approved", "role": "user", "projects": [] } ] }
```

No pagination, filtering or search parameter is accepted. A directory larger
than 200 cannot be read in full through this endpoint.

## GET /auth/people/:personId

Returns the person, the sign-in identities linked to them, and the identifiers
that resolve to them.

| Field | Detail |
|-------|--------|
| Person fields | As the table above |
| `identities` | One entry per sign-in method, newest link first |
| `identifiers` | One entry per address, phone number or provider subject |

Each identity carries `uid`, `provider`, `email`, `linkedAt`, a readable
`providerLabel`, and the provider's `subject`.

Each identifier carries `type`, `value`, `verified` and `source`. An identifier
with `verified: false` was imported or typed rather than proved. It suggests a
merge and never resolves a sign-in.

| Condition | Status | Body |
|-----------|--------|------|
| No such person | 404 | `{"error":"Not found"}` |

## POST /auth/people

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `name` | string | Yes | |
| `email` | string | No | `null` |
| `status` | string | No | `pending` |
| `role` | string | No | `user` |
| `projects` | array | No | `[]` |
| `groups` | array | No | `[]` |
| `tags` | array | No | `[]` |

| Condition | Status | Body |
|-----------|--------|------|
| Created | 200 | `{"ok":true,"personId":"…"}` |
| `name` missing | 400 | `{"error":"name required"}` |

A person created here holds no sign-in identity. Link one, or let the person
sign in and be matched on a verified identifier.

## PATCH /auth/people/:personId

Accepts `name`, `email`, `avatar`, `status`, `role`, `projects`, `groups` and
`tags`. Any other field is discarded silently.

| Condition | Status | Body |
|-----------|--------|------|
| Updated | 200 | `{"ok":true,"syncedFirebase":["…"],"firebaseSyncErrors":[]}` |
| No recognised field supplied | 400 | `{"error":"no valid fields"}` |

Changes are pushed to every linked sign-in identity. `syncedFirebase` lists the
identities updated and `firebaseSyncErrors` lists those that failed with the
reason. A 200 with a non-empty error list means the person was updated and at
least one identity was not.

| Change | Effect on sign-in |
|--------|-------------------|
| `status` set to `approved` | Gated endpoints begin accepting the person |
| `status` set to `rejected` | Linked sign-in identities are disabled |
| `projects` changed | Applies at the next request. Sessions are not re-issued |
| `role` set to `admin` | Grants every project and this page |

## POST /auth/people/:personId/link

Attaches an existing sign-in identity to a person.

| Field | Type | Required | Detail |
|-------|------|----------|--------|
| `uid` | string | Yes | Identity to attach |
| `provider` | string | No | Recorded label. Derived when omitted |
| `email` | string | No | Recorded address. Derived when omitted |

| Condition | Status | Body |
|-----------|--------|------|
| Linked | 200 | `{"ok":true}` |
| `uid` missing | 400 | `{"error":"uid required"}` |
| No such person | 404 | `{"error":"person not found"}` |
| Identity already belongs to another person | 409 | `{"error":"uid already linked to a different person"}` |

## DELETE /auth/people/:personId/identity/:uid

Unlinks a sign-in identity. The identity is removed from the person, the person
is retained.

| Condition | Status | Body |
|-----------|--------|------|
| Unlinked | 200 | `{"ok":true}` |
| Identity does not exist, or belongs to another person | 404 | `{"error":"Identity not found for this person"}` |

Unlinking does not remove the identifiers that resolve to the person. An address
or provider subject already claimed continues to resolve, so an unlinked account
can re-link itself by signing in again.

## POST /auth/sync/firebase

Walks every sign-in account and reconciles it against people. Takes no body.

```json
{ "ok": true, "scanned": 0, "linked": 0, "createdPeople": 0, "updatedIdentities": 0 }
```

| Property | Detail |
|----------|--------|
| Matching | An unlinked account is matched to a person by email address alone |
| Creation | An account matching nothing creates a person with status `pending` and the tag `imported-firebase` |
| Duration | Sequential per account. Large directories exceed the proxy timeout before finishing |
| Resumption | None. A timed-out run leaves partial results and must be restarted |

Matching by address alone is weaker than the rule applied at sign-in, where only
a proved identifier resolves a person. Run this only against a directory whose
addresses are trusted.

## POST /auth/sync/carddav

Imports contacts from the configured address books into people. Takes no body.

```json
{ "ok": true, "scanned": 0, "updatedPeople": 0, "createdPeople": 0, "syncedFirebase": 0, "syncErrors": [] }
```

| Condition | Status | Body |
|-----------|--------|------|
| Address book access not configured | 400 | `{"error":"…"}` |

Existing people are matched by email address and gain the tag `carddav-sync`.
Unmatched contacts create people with status `pending`. Contacts with no address
are skipped.

## POST /auth/provision

Retained for compatibility. Updates the person behind a sign-in identity.

| Field | Type | Required |
|-------|------|----------|
| `uid` | string | Yes |
| `status` | string | No |
| `projects` | array | No |
| `role` | string | No |
| `email` | string | No |

| Condition | Status | Body |
|-----------|--------|------|
| Updated | 200 | `{"ok":true}` |
| `uid` missing | 400 | `{"error":"uid required"}` |

Prefer `PATCH /auth/people/:personId`. This endpoint does not push changes to
linked sign-in identities and does not report what it changed.

## Constraints

| Constraint | Detail |
|------------|--------|
| Deletion | No endpoint deletes a person or an identifier |
| Pagination | Not available on any list |
| Search | Not available. Lookup is by `personId` only |
| Audit trail | Not exposed. Changes are not attributed to the admin who made them |
| Concurrency | Last write wins. Two admins editing one person overwrite each other |

## Related

- [Authentication](authentication.md) covers the admin gate.
- [Sessions and sign-in](sessions.md) covers how a person is created at sign-in.
- [Diagnostics](diagnostics.md) covers failed links and partial syncs.
