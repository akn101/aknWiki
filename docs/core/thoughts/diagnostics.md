---
sidebar_position: 4
title: Diagnostics
---

# Diagnostics

Observed conditions and their resolutions.

## Reading

| Condition | Cause | Resolution |
|-----------|-------|------------|
| `nothing here yet` | No published notes exist | Submit the first note |
| Board area renders empty with no message | Note retrieval failed. Failures are silent | Reload. Change network or browser if it persists |
| Board renders in one column on a wide screen | Column count is set at load from window width | Reload after resizing |
| A note that was present has disappeared | It was withdrawn by a moderator | No action available |

## Submitting

| Condition | Cause | Resolution |
|-----------|-------|------------|
| **send** has no effect | Field is empty or whitespace only | Enter text |
| Note appears truncated | Submission exceeded 160 characters | Shorten and resubmit |
| Dialog closed before sending | `Escape`, **cancel**, or an outside click was registered | Reopen and re-enter. Drafts are not retained |
| Confirmation shown but note absent from board | Awaiting review, or rejected | Status is not exposed. Resubmit if required |

## Moderation

| Condition | Cause | Resolution |
|-----------|-------|------------|
| Sign-in returns to akn ID repeatedly | Account lacks a scope for this site | Request the `thoughts` scope |
| `/admin` prompts for sign-in after previous use | Session passed 30 days | Sign in again |
| Removal withdrew the wrong note | The page was stale. Removal acts on list position | Reload before each removal |
| Queue shows a note already handled | Another moderator acted concurrently | Reload |

## Escalation

Conditions not resolved by the above should be reported to the site operator.
Include the URL, the browser, and the time the condition occurred.

Service availability is published at https://status.akn.me.uk.

## Related

- [Overview](overview.md)
- [Using the board](using.md)
- [Moderation](moderation.md)
