---
sidebar_position: 3
title: Incidents
---

# Incidents

The Incident Reports section sits at the foot of the page, below the service
cards. It holds two lists: Active Incidents and Past Incidents.

Incidents arise in two ways. Most are raised automatically from recorded check
failures. An operator can also declare one, in which case the wording is the
operator's own.

## What an incident record contains

| Field | Shown for | Contents |
|-------|-----------|----------|
| Date | All incidents | The day the first failed check was recorded, as `18 Jun 2026` |
| Service | All incidents | The name the affected service is monitored under, on a grey badge |
| Status | Active incidents | `investigating` on a red badge, or `monitoring` on a yellow badge |
| Title | All incidents | The service name and the severity wording |
| Description | All incidents | The affected address, the duration measured, and the start time in GMT |
| ETA | Active incidents | An expected resolution time |
| Resolution | Past incidents | A timestamp in GMT followed by `Service restored` |

## Automatic titles and wording

Automatic incidents take their title from the measured duration.

| Measured duration | Title | Description pattern |
|-------------------|-------|---------------------|
| Under one hour | `<service> Service Disruption` | Reports downtime starting at a given time |
| One hour to 24 hours | `<service> Extended Outage` | Reports an approximate number of hours |
| Over 24 hours | `<service> Multi-Day Outage` | Reports a number of days |

## How an incident is raised

| Rule | Detail |
|------|--------|
| Threshold | Two consecutive failed checks for the same service |
| Effect of the threshold | A single failed check never produces an incident |
| Active | The most recent failure is within the past two hours |
| Past | The most recent failure is more than two hours old |
| Excluded | The external reference address raises no incidents |

Because checks are commonly one to two hours apart, an interruption must
persist for hours before it is recorded as an incident. Short interruptions
appear on the history bar without producing an incident entry.

## How history is presented

| Property | Detail |
|----------|--------|
| Order | Newest first, in both lists |
| Grouping | By incident, not by service. A service with repeated outages appears repeatedly |
| Retention | An incident is listed for as long as the check history covering it is retained |
| Empty active list | Displays `All systems operational` |
| Empty past list | Displays `No past incidents` |
| Automatic scroll | When an active incident exists, the page scrolls to the incident section shortly after loading |
| Pagination | None. All retained incidents are listed at once |

An incident moves from Active Incidents to Past Incidents on its own once the
service answers again. No notice is issued.

## Interpreting a past incident

| Element | How to read it |
|---------|----------------|
| Start time | The time of the first failed check. The interruption began at some point after the previous successful check |
| Duration | Measured from the first failed check to the last. It understates the true interruption by up to the gap between checks |
| Restoration time | The time of the last failed check. The service answered again at some point before the next recorded check |
| Address shown as `Unknown URL` | The service is no longer monitored. Its past incidents remain listed |
| Approximate hours or days | Rounded. Treat the figure as indicative |

Durations state when the address stopped answering, not what caused it. The
page carries no cause, no affected-feature breakdown, and no follow-up notes.

## ETA on active incidents

An automatic incident carries an expected resolution time set 24 hours after
the incident was raised. The figure is a fixed placeholder rather than an
estimate of the work involved.

> Treat the ETA as a review point, not a commitment.

## Related

- [Reading the page](using.md) covers the service cards and the history bar.
- [Operator tasks](operators.md) covers declaring and resolving incidents.
- [Diagnostics](diagnostics.md) covers incidents that do not appear as expected.
