---
sidebar_position: 2
title: Reading the page
---

# Reading the page

The page loads on arrival at https://status.akn.me.uk. No action is required.
A spinner and the message `Loading status information...` appear while the
recorded results are read.

## Layout

| Region | Contents |
|--------|----------|
| Top | The akn logo |
| Middle | One card for each monitored service |
| Bottom | Incident Reports, split into Active Incidents and Past Incidents |

| Viewport | Service card columns |
|----------|----------------------|
| Wider than 800 pixels | 2 |
| 800 pixels or narrower | 1 |

The page follows the light or dark setting of the device.

## Service cards

Each card carries five elements.

| Element | Position | Contents |
|---------|----------|----------|
| Service name | Top left | The name the service is monitored under |
| State indicator | Top right | A coloured dot for the current day |
| Address | Below the name | The address that is requested, as a link |
| Uptime figure | Right of the address | A percentage, labelled as the last 30 days |
| History bar | Below | 30 segments, oldest at the left, today at the right |

## State indicators

The dot and every history segment use the same four states. Hover the dot to
read its wording.

| Colour | Label | Meaning |
|--------|-------|---------|
| Green | Fully Operational | Every check recorded that day succeeded |
| Orange | Partial Outage | Some checks failed. At least 30 per cent succeeded |
| Red | Major Outage | Fewer than 30 per cent of checks succeeded |
| Grey | No Data Available | No check was recorded that day |

The dot reflects the current day only. A service that failed yesterday and is
answering today shows green with a red segment behind it.

Grey is common in the first hours of a day, before the first check of that day
is recorded.

## History bar

Each segment is one day. Hover a segment to display the date, the state, and a
sentence describing it.

| State | Sentence shown |
|-------|----------------|
| Green | No downtime recorded on this day. |
| Orange | Partial outages recorded on this day. |
| Red | Major outages recorded on this day. |
| Grey | No Data Available: Health check was not performed. |

The bar always shows 30 days. Days before monitoring began for that service
appear grey.

## Uptime figure

The figure counts every successful check against every check recorded for that
service.

| Property | Detail |
|----------|--------|
| Label shown | `in the last 30 days` |
| Period actually covered | Every check still retained for the service, which extends beyond 30 days |
| Value when no results can be read | `--%` |
| Rounding | Two decimal places |

Read the figure as long-run availability rather than a strict 30 day measure.

## Check frequency and freshness

| Property | Detail |
|----------|--------|
| Scheduled checks | Three times an hour |
| Recorded in practice | Around 13 a day, so successive results are commonly one to two hours apart |
| Attempts per check | Up to four, spaced five seconds apart. A failure is recorded only if all four fail |
| Time limit per attempt | 10 seconds |
| Page refresh | None. The page reads results once, when it loads |

An interruption shorter than about a minute, or one falling between two
recorded checks, does not appear on the page. Reload the page to pick up newer
results.

## Monitored services

| Name on the page | Address monitored | Description |
|------------------|-------------------|-------------|
| Halcyon | https://akn.me.uk | Portfolio and commissions site |
| Iris | https://iris.akn.me.uk | Not documented |
| Letters | https://letters.akn.me.uk | Not documented |
| EchelonAPI | https://api.akn.me.uk | Shared services used by akn products |
| EtonSTEM | https://etonstem.com | Not documented |
| aknWiki | https://docs.akn.me.uk | This documentation site |
| PathwayWeb | https://tpi.akn.org.uk | The Pathway Initiative tutoring site |
| Startpage | https://startpage.akn.me.uk | Browser start page |
| StatusPage | https://status.akn.me.uk | This status page |
| Thoughts | https://thoughts.akn.me.uk | aknThoughts bulletin board |
| Auracare | https://auracare.org.uk | AuraCare site |
| Auracle | https://buyauracle.com | Not documented |
| worldclock | http://worldclockapi.com/api/json/utc/now | External address used as a reference. Excluded from incident reporting |

The list changes when an operator adds or removes a service. A newly added
service shows a grey bar and `--%` until its first checks are recorded.

## When a service shows down

1. Hover the dot to confirm the wording. Orange and red are distinct states.
2. Read the history bar to establish whether the failure started today.
3. Read Active Incidents for an entry naming that service.
4. Reload the page. The state shown was read when the page loaded.
5. Try the service address directly. The check tests reachability, not
   function.

If no incident is listed and the failure persists, report it to the site
operator with the service name and the time.

## Related

- [Overview](overview.md) covers what a check does and does not establish.
- [Incidents](incidents.md) covers the incident sections at the foot of the page.
- [Diagnostics](diagnostics.md) covers conditions encountered while reading the page.
