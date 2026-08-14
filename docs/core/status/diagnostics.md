---
sidebar_position: 5
title: Diagnostics
---

# Diagnostics

Observed conditions and their resolutions.

## Loading the page

| Condition | Cause | Resolution |
|-----------|-------|------------|
| `Loading status information...` remains on screen | Recorded results are still being read | Wait, then reload |
| No service cards appear and only the incident section is shown | The list of monitored services could not be read | Reload. Change network or browser if it persists |
| Browser tab is titled `Checkmate` | The page carries a leftover title | None required. The page is aknStatus |
| The page jumps to the incident section on load | An active incident exists. The page scrolls there automatically | Scroll back up |
| States look older than expected | The page reads results once, when it loads | Reload |

## Service states

| Condition | Cause | Resolution |
|-----------|-------|------------|
| Dot is grey and labelled `No Data Available` | No check has been recorded for the current day | Read the history bar for the preceding days |
| Card shows a grey bar and `--%` | No results are retained for that service, or it was added recently | Wait for checks to accumulate |
| Service is red but the address opens normally | The service answered again after the last recorded check | Reload later, or use the service directly |
| Service is green but a feature inside it fails | Only reachability of the published address is checked | Report the fault to the site operator |
| A service you expect is absent from the page | It is not monitored, or an operator removed it | Ask the site operator to add it |
| A segment is orange for a day that seemed normal | Some checks failed that day. At least 30 per cent succeeded | None available. Day states are not itemised |

## Uptime figure

| Condition | Cause | Resolution |
|-----------|-------|------------|
| Figure disagrees with the 30 day history bar | The figure counts every retained check, covering a longer period than 30 days | Read the bar for the recent picture |
| Figure reads 100 per cent despite a remembered outage | The interruption fell between two recorded checks, or predates the retained history | None available |
| Figure reads `--%` | The recorded results for that service could not be read | Reload |

## Incidents

| Condition | Cause | Resolution |
|-----------|-------|------------|
| Both incident sections read `None recorded` | Incident data could not be loaded. Loaded sections read `All systems operational` and `No past incidents` | Reload |
| A service is red but no incident is listed | Fewer than two consecutive failed checks have been recorded | Check again after the next recorded check |
| An incident remains active after the service recovered | An incident stays active until its most recent failure is more than two hours old | Wait for the next update |
| The expected resolution time has passed | The time is a fixed placeholder set 24 hours after the incident was raised | Disregard the figure |
| An incident names a service that has no card | The service is no longer monitored. Its past incidents remain listed | None required |
| An incident shows `Unknown URL` | The affected service is no longer monitored | None required |
| A brief outage never produced an incident | Two consecutive failed checks are required | None available |

## Operator panel

| Condition | Cause | Resolution |
|-----------|-------|------------|
| `/admin` returns to sign-in repeatedly | The account is not permitted to operate this page | Request access from the site operator |
| A red message appears after selecting a control | The action was rejected | Check the values entered and try again |
| Controls do nothing when selected | An action is in progress and controls are disabled | Wait for the confirmation message |
| **create incident** has no effect | **title** or **service** is empty | Complete both fields |
| A created incident is absent from the public page | The public page reads incidents when it loads | Reload the public page |
| A created incident disappeared later | Incident records are rebuilt from recorded check history | Declare it again if it is still required |
| A removed service still shows a card | The public page was loaded before the removal | Reload the public page |
| An incident carries the wrong wording | Incidents cannot be edited after creation | Resolve it and declare a replacement |

## Escalation

Conditions not resolved by the above should be reported to the site operator.
Include the service name, the state shown, and the time the condition occurred.

## Related

- [Overview](overview.md)
- [Reading the page](using.md)
- [Incidents](incidents.md)
- [Operator tasks](operators.md)
