---
sidebar_position: 6
title: Notifications, calendar and status
---

# Notifications, calendar and status

Three groups serve the data behind akn's own sites. Notifications and calendar
are gated by the `startpage` project grant. Status is gated by the admin role or
the `status` grant.

| Method | Path | Credential |
|--------|------|-----------|
| POST | `/startpage/notify` | API key |
| GET | `/startpage/notifications` | Session cookie or bearer ID token, plus the `startpage` grant |
| GET | `/calendar/events` | Session cookie or bearer ID token, plus the `startpage` grant |
| GET | `/calendar/upcoming-locations` | None |
| GET | `/status` | Session cookie, admin role or `status` grant |
| POST | `/status/incident` | Session cookie, admin role or `status` grant |
| PATCH | `/status/incident` | Session cookie, admin role or `status` grant |
| POST | `/status/url` | Session cookie, admin role or `status` grant |
| DELETE | `/status/url` | Session cookie, admin role or `status` grant |

## POST /startpage/notify

Submits a notification. Server to server, with no user session.

| Field | Type | Required | Detail |
|-------|------|----------|--------|
| `title` | string | Yes | |
| `body` | string | Yes | |
| `source` | string | No | `android` or `openclaw`. Any other value is stored as `other` |

| Condition | Status | Body |
|-----------|--------|------|
| Accepted | 200 | `{"ok":true,"id":123}` |
| Key missing or wrong | 401 | `{"error":"Unauthorized"}` |
| `title` or `body` missing | 400 | `{"error":"title and body required"}` |
| Store rejected the write | 500 | `{"error":"…"}` |

No length limit is enforced and no deduplication is applied. A repeated
submission creates a second notification.

## GET /startpage/notifications

| Parameter | In | Required | Detail |
|-----------|----|----------|--------|
| `since` | Query | No | Milliseconds since the epoch. Returns notifications created after that instant |

```json
{ "notifications": [ { "id": 1, "title": "…", "body": "…", "source": "android", "created_at": "…" } ] }
```

| Property | Detail |
|----------|--------|
| Ordering | Oldest first, with and without `since` |
| Limit | 20 per request |
| Without `since` | The 20 most recent notifications |
| With `since` | The 20 oldest notifications after that instant |
| Pagination | Not available. Poll with `since` set to the newest `created_at` already held |

The feed is not per-caller. Every holder of the `startpage` grant reads the same
notifications.

| Condition | Status | Body |
|-----------|--------|------|
| Store rejected the read | 500 | `{"error":"…"}` |

## GET /calendar/events

Returns the owner's calendar for the coming week.

```json
{ "events": [ { "uid": "…", "summary": "…", "location": "…", "joinUrl": "…", "start": "…", "end": "…", "allDay": false } ] }
```

| Property | Detail |
|----------|--------|
| Window | Now to seven days ahead |
| Limit | 10 events, earliest first |
| `joinUrl` | Present when the event carries a conference link |
| `location` | Present when the event carries one |
| Recurring events | Expanded by the upstream calendar within the window |

An upstream failure, and a service with no calendar configured, both answer 200
with `{"events":[]}`. An empty array does not mean the week is free.

## GET /calendar/upcoming-locations

Public. Returns places inferred from the calendar over the coming month.

```json
{
  "locations": [
    {
      "city": "Tokyo",
      "country": "Japan",
      "when": "3 Sep",
      "start": "…",
      "end": "…",
      "tentative": false,
      "status": "confirmed",
      "confidence": "high",
      "confidenceScore": 0.95
    }
  ]
}
```

| Property | Detail |
|----------|--------|
| Window | 31 days ahead |
| Limit | 12 entries, earliest first, one per city per day |
| `status` | `confirmed` or `tentative` |
| `confidence` | `high`, `medium` or `low` |
| `confidenceScore` | 0 to 1 |

Places are inferred from event text against a fixed list of known cities. An
event elsewhere produces no entry. Events that read as remote, and events whose
location is a URL, are skipped.

A failure answers 200 with `{"locations":[]}`.

## GET /status

Returns the incident record and the list of monitored URLs.

```json
{
  "incidents": { "active": [], "resolved": [] },
  "urls": [ { "name": "…", "url": "https://…" } ],
  "incidentsSha": "…",
  "urlsSha": "…"
}
```

The `incidentsSha` and `urlsSha` fields identify the revision each list was read
from. They are informational. No endpoint accepts them back.

## POST /status/incident

| Field | Type | Required |
|-------|------|----------|
| `title` | string | Yes |
| `service` | string | Yes |
| `description` | string | No |
| `url` | string | No |

| Condition | Status | Body |
|-----------|--------|------|
| Created | 200 | `{"ok":true,"incident":{…}}` |
| `title` or `service` missing | 400 | `{"error":"title and service required"}` |

The incident is created with status `investigating` and added to the top of the
active list. Its `incidentId` is derived from the service name and the creation
time.

## PATCH /status/incident

| Field | Type | Required | Detail |
|-------|------|----------|--------|
| `incidentId` | string | Yes | From the active list |
| `action` | string | Yes | `resolve` or `update` |
| `updates` | object | Conditional | Fields to merge. Required in effect for `update` |

| Condition | Status | Body |
|-----------|--------|------|
| Applied | 200 | `{"ok":true}` |
| `incidentId` or `action` missing | 400 | `{"error":"incidentId and action required"}` |
| No active incident with that id | 404 | `{"error":"not found"}` |
| `action` is neither value | 400 | `{"error":"unknown action"}` |

`resolve` moves the incident to the resolved list, stamps the end time, and
drops its status field. A resolved incident cannot be reopened through the API.

`update` merges `updates` into the active incident with no field validation. A
misspelled key is written as a new field.

## POST /status/url

| Field | Type | Required |
|-------|------|----------|
| `name` | string | Yes |
| `url` | string | Yes |

| Condition | Status | Body |
|-----------|--------|------|
| Added | 200 | `{"ok":true}` |
| A field is missing | 400 | `{"error":"name and url required"}` |

Adding a name that already exists appends a second entry rather than replacing
the first.

## DELETE /status/url

Takes a JSON body, not a query parameter.

| Field | Type | Required |
|-------|------|----------|
| `name` | string | Yes |

| Condition | Status | Body |
|-----------|--------|------|
| Removed | 200 | `{"ok":true}` |
| `name` missing | 400 | `{"error":"name required"}` |

Removing a name that is not present answers 200 and changes nothing.

## Status access constraint

The `/status` endpoints decide access from a legacy account record rather than
the person record used everywhere else. An account created after the identity
migration can hold the admin role, pass every other gated endpoint, and still be
refused here with 403.

## Concurrency

Incident and URL changes are read-modify-write against a single stored revision.
Two administrators acting at the same time can produce a failed write, or a
change that overwrites the other. Reload before each change.

## Related

- [Authentication](authentication.md) covers project grants.
- [Location](location.md) covers the public location endpoints.
- [Diagnostics](diagnostics.md) covers empty feeds and refused status access.
