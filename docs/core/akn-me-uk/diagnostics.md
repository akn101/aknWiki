---
sidebar_position: 6
title: Diagnostics
---

# Diagnostics

Observed conditions and their resolutions.

## Arrival and navigation

| Condition | Cause | Resolution |
|-----------|-------|------------|
| The opening screen advances before it is read | It advances five seconds after loading | Open **strive for excellence** at the foot of the side menu to return to it |
| No menu button on the opening screen | The opening screen carries no navigation | Select anywhere to advance, or wait |
| `Cmd`+`K` has no effect on the opening screen | The command palette is not available there | Advance to Home first |
| The menu button cannot be found on a wide window | The button retracts against the left edge shortly after the section loads | Move the pointer to the left edge at mid height |
| The command palette shows `No results` | No section, project, or experiment matches the text | Clear the field to see every group |
| A project is missing from the command palette | The entry is withheld from the current visitor | Enter an access code, or sign in with akn ID |
| `Loading…` remains on screen | The section has not finished opening | The indicator clears after seven seconds. Reload if the section has not opened |
| No theme button in the header | The control is present only when the device reports a dark colour scheme | Change the device colour scheme |
| No theme button anywhere on Home or Letters | Those sections carry no header | Switch theme from another section |

## Home

| Condition | Cause | Resolution |
|-----------|-------|------------|
| Location reads `Location unavailable` | The location could not be retrieved | Reload. No further action is available |
| Location reads `last seen in <place>` | The most recent reading is too old to stand as current | None |
| The clock does not match local time | The clock runs in the timezone of the last known location | None |
| `No recent Dawarich locations` in the panel | No past locations are recorded | None |
| The location panel does not open | On wide windows the panel opens on hover, on narrow ones on selection | Select the location label |
| `last visit from` is absent | No previous visit is recognised for this browser | None |
| A shimmering bar sits where the status strip should be | The strip has not finished resolving | Wait. Reload if it does not settle |

## Work and Flair

| Condition | Cause | Resolution |
|-----------|-------|------------|
| `Nothing here.` under a tab | No project matches that tab | Select **All** |
| A project name opens nothing | The entry carries no destination | None |
| An experiment does not respond to the pointer | Interactive experiments run inside their own card | Select inside the card before interacting |
| Audio will not play | The waveform has not finished loading | Wait for the waveform to appear, then select play |
| A project visible earlier is now absent | The access that revealed it has expired | Enter the access code again |
| The grid shows fewer columns than expected | Column count follows window width | Widen the window |

## Photography

| Condition | Cause | Resolution |
|-----------|-------|------------|
| Photographs stay blurred | The full images are still downloading | Wait. Change network if it persists |
| A photograph fails to appear in the viewer | The full size image could not be retrieved | Close the viewer and select the photograph again |

## Letters

| Condition | Cause | Resolution |
|-----------|-------|------------|
| A letter you were sent is not in the list | It is restricted and the browser holds no access for it | Enter the access code, or sign in with akn ID |
| `This letter is restricted. Please enter the access code to view.` remains after the dialog is closed | The dialog does not reopen from that screen | Return to the list and select the letter again |
| The body is blank after access was granted | Retrieval of the text failed. Failures are silent | Reload the letter |
| No Contents sidebar | The piece carries no headings, or the window is too narrow | Widen the window |
| `No posts yet. Check back soon!` | No letters were retrieved | Reload. Report it if it persists |

## Access

| Condition | Cause | Resolution |
|-----------|-------|------------|
| The dialog closes with no message after **Next** | The code was rejected | Enter it again. Use `/access` in the command palette for a stated result |
| `Invalid access code` | The code is wrong or no longer active | Confirm the code with whoever issued it |
| `Access not granted for halcyon.` | The akn ID account holds no grant for this site | Request access to this site through akn ID |
| Sign-in returns to akn ID repeatedly | The akn ID session was not established | Complete sign-in at akn ID, then open the site again |
| Protected entries disappeared during a visit | Code access lasts 24 hours | Enter the code again |
| No lock button on Home | Home carries no header | Open any other section, or type `/access` in the command palette |
| Access cannot be given up | Removing access is not available from the interface | Wait for code access to expire, or clear site data in the browser |

## Escalation

Conditions not resolved by the above should be reported to the site operator.
Include the section, the browser, and the time the condition occurred.

Service availability is published at https://status.akn.me.uk.

## Related

- [Overview](overview.md)
- [Using the site](using.md)
- [Sections](sections.md)
- [Protected content](protected-content.md)
- [Letters](letters.md)
