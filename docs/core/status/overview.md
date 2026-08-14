---
sidebar_position: 1
title: Overview
---

# aknStatus

| | |
|---|---|
| URL | https://status.akn.me.uk |
| Description | Public availability dashboard for akn services, with a 30 day history and incident record |
| Access | Public read. Incident and service administration require sign-in |
| Pricing | Free |

## Overview

aknStatus allows users to check whether akn services are reachable, view 30
days of recorded availability for each one, and read the record of active and
past incidents. No account is required to read any part of the page.

Availability is established by requesting each monitored address on a schedule
and recording whether it answered. A service marked operational answered its
last request.

## Capabilities

| Capability | Availability |
|------------|--------------|
| View current state of each monitored service | Any visitor |
| View 30 days of recorded availability | Any visitor |
| View the uptime percentage for a service | Any visitor |
| Read active and past incidents | Any visitor |
| Declare and resolve incidents | Signed-in operators at `/admin` |
| Add and remove monitored services | Signed-in operators at `/admin` |
| Subscribe to alerts or notifications | Not available |
| Search, filter, or reorder the service list | Not available |
| Change the history window from 30 days | Not available |
| Refresh automatically while the page is open | Not available |
| Report a problem from the page | Not available |
| View response times or performance figures | Not available |

## What a check establishes

| Property | Detail |
|----------|--------|
| Signal recorded | Whether the address answered a request |
| Answer accepted | A normal response or a redirect counts as success |
| Not recorded | Page content, correctness, speed, or whether a sign-in works |
| Scope | The published address only. Individual features behind it are not tested |

A service can appear operational while a feature inside it is broken.

## Restricted areas

The operator panel is at `/admin`. Visitors without a valid session are sent to
akn ID to sign in and returned to the panel afterwards.

## Next steps

- [Reading the page](using.md) covers indicators, history, and the monitored services.
- [Incidents](incidents.md) covers what an incident record contains and how to read it.
- [Operator tasks](operators.md) covers declaring and resolving incidents.
- [Diagnostics](diagnostics.md) lists observed conditions and resolutions.

## Related products

- [aknID](../../platform/akn-id/overview.md), access control for the operator panel
