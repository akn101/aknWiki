---
sidebar_position: 7
title: Location
---

# Location

Public endpoints reporting where the owner is, and recording where visitors call
from. None of them accepts a credential.

| Method | Path | Purpose |
|--------|------|---------|
| GET | `/location/current` | Cached location summary |
| GET | `/location/live` | Location summary fetched from the upstream on every call |
| GET | `/location/tooltip` | Summary with history, timezone and confidence |
| GET | `/location/history` | Recent distinct cities |
| GET | `/location/last-visit` | City the previous visitor called from |
| POST | `/location/visitor-context` | Previous visitor, then record the current one |
| POST | `/location/visit` | Record the current visitor |

## Failure behaviour

Every endpoint on this page answers 200. A failed upstream call, an
unconfigured upstream and a genuine empty result are reported the same way,
through the body.

| Endpoint | Body on failure |
|----------|-----------------|
| `/location/current`, `/location/live` | Last known summary with `stale: true`, or `location: "Location unavailable"` |
| `/location/tooltip` | Last known payload with `stale: true`, or the unavailable summary with empty history |
| `/location/history` | `{"locations":[]}` |
| `/location/last-visit` | Last known visit, or `city: "Unknown"` |
| `/location/visitor-context` | `recordedVisit: null` |
| `/location/visit` | `{"ok":false,"reason":"location_unavailable"}` or `{"ok":false,"reason":"tracking_failed"}` |

Treat `stale`, `confidence` and `source` as the error channel.

## GET /location/current

```json
{
  "location": "Shinjuku, Tokyo, Japan",
  "tooltip": "In Shinjuku, Tokyo, Japan earlier today",
  "updatedAt": "2026-08-14T09:12:00.000Z",
  "source": "…",
  "latitude": 35.69,
  "longitude": 139.7
}
```

| Field | Detail |
|-------|--------|
| `location` | Neighbourhood, city and country, joined by commas. Whichever parts are known |
| `tooltip` | Sentence combining the place and how long ago it was recorded |
| `updatedAt` | When the position was recorded upstream. Null when the upstream gave no time |
| `source` | Identifier of the upstream that produced the record |
| `latitude`, `longitude` | Numbers, or absent when the upstream gave none |
| `stale` | Present and true only when a live value could not be obtained |

The cached value is served for 30 minutes and refreshed behind the response.
A caller polling faster than that receives the same body.

## GET /location/live

Same body as `/location/current`, fetched from the upstream on every call and
without the cache. Slower, and subject to the upstream timeout. Use it only when
a caller needs the newest fix rather than the cheapest.

## GET /location/tooltip

The composed payload, including past and future places.

```json
{
  "location": "Tokyo, Japan",
  "tooltip": "In Tokyo, Japan earlier today",
  "lastUpdate": "earlier today",
  "updatedAt": "2026-08-14T09:12:00.000Z",
  "ageMs": 7200000,
  "confidence": "recent",
  "stale": false,
  "builtAt": "2026-08-14T11:00:00.000Z",
  "timezone": "Asia/Tokyo",
  "source": "…",
  "historyPast": [ { "city": "London, United Kingdom", "when": "a few days ago" } ],
  "historyFuture": [ { "city": "Dublin", "when": "3 Sep", "country": "Ireland", "at": "…", "tentative": false, "status": "confirmed", "confidence": "high", "confidenceScore": 0.95 } ]
}
```

| Field | Detail |
|-------|--------|
| `lastUpdate` | Phrase such as `just now`, `earlier today`, `a few days ago` |
| `ageMs` | Age of the position in milliseconds. Null when no time is known |
| `builtAt` | When this payload was composed |
| `cacheAgeMs` | Present when the payload was served from cache |
| `timezone` | IANA name, or null |
| `historyPast` | Up to 10 recent cities, excluding the current one |
| `historyFuture` | Up to 10 upcoming places from the calendar, merged and deduplicated |

| `confidence` | Meaning |
|--------------|---------|
| `live` | Recorded within the last hour |
| `recent` | Recorded within the last 24 hours |
| `stale` | Older than 24 hours. `stale` is also true |
| `unknown` | A place is known, but not when it was recorded |

`unknown` is not treated as stale. Present it as a place without a time rather
than suppressing it.

The payload is rebuilt on a timer and served from cache. A cached payload older
than 24 hours is rebuilt before the response is sent, which makes that request
slower.

## GET /location/history

```json
{ "locations": [ { "city": "London, United Kingdom", "when": "a few days ago", "updatedAt": "…", "source": "…" } ] }
```

| Property | Detail |
|----------|--------|
| Window | 21 days |
| Limit | Three distinct cities, newest first |
| Duplicates | Removed. One entry per city and country pair |

Positions the upstream reports without a place name are resolved against a
geocoder, subject to a per-request budget. Beyond that budget a position is
skipped rather than delayed, so a sparse history is expected rather than
exceptional.

## GET /location/last-visit

Returns the city the previous visitor called from.

```json
{ "city": "Dublin", "country": "Ireland", "updatedAt": "…", "source": "…" }
```

| Field | Detail |
|-------|--------|
| `city` | `Unknown` when no visit has been recorded |
| `country` | Null when the lookup returned none |
| `source` | `fallback` indicates no stored visit was available |

The value is cached for five minutes and refreshed behind the response.

## POST /location/visitor-context

Returns the previous visitor, then records the caller as the current one. Takes
no body.

```json
{
  "previousVisit": { "city": "Dublin", "country": "Ireland", "updatedAt": "…", "source": "…" },
  "recordedVisit": { "city": "Tokyo", "country": "Japan", "updatedAt": "…", "source": "…" }
}
```

`recordedVisit` is null when the caller's address could not be resolved to a
city. `previousVisit` is always present.

## POST /location/visit

Records the caller as the current visitor without returning the previous one.
Takes no body.

| Condition | Body |
|-----------|------|
| Recorded | `{"ok":true,"city":"…","country":"…","updatedAt":"…","source":"…"}` |
| Address not resolvable to a city | `{"ok":false,"reason":"location_unavailable"}` |
| Recording failed | `{"ok":false,"reason":"tracking_failed"}` |

## Visitor records

| Property | Detail |
|----------|--------|
| What is recorded | City and country only. The address itself is not stored |
| Where it comes from | The forwarded client address on the request |
| Private addresses | Ignored. A request from a private range records nothing |
| Retention | One record. Each visit overwrites the last |
| Visibility | The recorded city is returned to the next caller of `/location/last-visit` |
| Removal | Not available. There is no endpoint to clear or suppress a record |

A caller sending `POST /location/visit` on behalf of an end user publishes that
user's city to the next visitor.

## Related

- [Notifications, calendar and status](feeds.md) covers the calendar the future places come from.
- [Errors](errors.md) covers why these endpoints never return an error status.
- [Diagnostics](diagnostics.md) covers stale and unavailable locations.
