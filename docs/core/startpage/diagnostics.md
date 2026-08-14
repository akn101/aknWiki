---
sidebar_position: 8
title: Diagnostics
---

# Diagnostics

Observed conditions and their resolutions.

## Opening and searching

| Condition | Cause | Resolution |
|-----------|-------|------------|
| The palette opens as soon as a key is pressed | Any single character opens the palette when no field is focused | Press `Escape`. Select a field before typing into it |
| `⌘K` does nothing | Focus is inside a field, or the browser has taken the shortcut | Select the search bar or the **⌘** button at the bottom right |
| A search opens nothing | Results open in a new tab, which the browser blocked | Allow new windows for this site |
| An address was searched for instead of opened | Text containing a space is always treated as a search | Remove the space, or enter the full address |
| No suggestions appear below a search | Suggestions require sign-in and a previous identical search | Sign in |
| `No results` | The entered text matches no command, link or search action | Clear the text and enter `/` to list the commands |

## Commands

| Condition | Cause | Resolution |
|-----------|-------|------------|
| `/camera` produces `No results` | Camera monitoring is switched off for this site | None. The command is listed but inactive |
| `/todo` accepted but the task never appears | Adding requires sign-in. The failure is silent | Sign in and enter it again |
| Completed tasks return after a reload | `/clear` requires sign-in. The removal was shown but not saved | Sign in and run `/clear` again |
| `/alarm` accepted but no alarm is listed | Not signed in, or the time was not entered as `HH:MM` | Sign in. Enter the time as digits, for example `/alarm 07:30` |
| `/display` returns to the access page | Display mode requires sign-in | Sign in, or use the fourth page section |
| The screen no longer dims at night | A level has been set with `/dim`, which replaces automatic dimming | Automatic dimming cannot be restored from the page. Clear the site data in the browser |

## Todos, timers and alarms

| Condition | Cause | Resolution |
|-----------|-------|------------|
| A running timer disappeared | Running timers are held only while the page is open | Stop timers before reloading or closing the tab |
| A saved session has no project | Nothing matched the label, or matching was unavailable | None from the page. See [Assistant](assistant.md) |
| Time appears as not matched to a project in This week | The sessions behind it were saved with no project | None from the page |
| An alarm did not sound | The page was not open, or it was never selected during the visit | Keep the page open. Select or tap it once so sound is permitted |
| An alarm sounded again the next day | Alarms repeat every day at the set time | Disable it with the dot, or remove it with **✕** |
| The Alarms widget reads `Log in to manage alarms` | Alarms are private to an account | Sign in |
| A habit mark disappeared | The mark was shown before it was saved, and saving failed | Mark it again once the connection returns |

## Widgets and data

| Condition | Cause | Resolution |
|-----------|-------|------------|
| Projects, GitHub, Calendar and This week are all empty | These tiles hold private data and are empty while signed out | Sign in |
| Weather reads `loading…` and does not change | The location or weather lookup failed. The failure is silent | Reload |
| Weather shows the wrong city | Location is approximate and taken from the network address | None. A different network or a VPN changes the result |
| Weather is stale during a long session | Weather is read once per visit | Reload |
| The calendar reports that it is not configured | The calendar connection has not been set up for this site | Report to the site operator |
| The Photos tile shows a setup message | No photos are available to this account | None. Photos cannot be added from the page |
| A task status change reverted | Changing tasks requires an administrator account. The change was shown before it was rejected | Request administrator access |
| A project or task added from the page vanished | Same cause as above | Request administrator access |
| Tile data is up to half an hour old | Widgets refresh every 30 minutes | Reload |
| `could not load` on a tile | The source did not answer | Reload. Report to the site operator if it persists |

## Display mode

| Condition | Cause | Resolution |
|-----------|-------|------------|
| Display mode opened on its own | Ten minutes passed without input, between 09:00 and 18:00 | Move the mouse or press `Escape` |
| Display mode never opens on its own | It does not open between 18:00 and 09:00 | Enter `/display`, or scroll to the fourth section |
| Panels stopped rotating | The pointer is over the panel, which pauses it | Move the pointer away |
| Panels show no content | The panels hold private data and are empty while signed out | Sign in |

## Installing and offline

| Condition | Cause | Resolution |
|-----------|-------|------------|
| No install control in the browser | The browser does not offer installation, or the page is already installed | Use the browser menu, or open the installed app |
| The page reloaded by itself | A new version was found and applied after ten minutes without input | None. This is expected |
| Changes made offline were lost | Editing requires a connection | Repeat the change once the connection returns |
| Old data is shown with no warning | Stored data is used when the connection fails, up to 24 hours old | Reload once the connection returns |
| The page is slow to appear | The connection is reachable but slow. Stored data is used after ten seconds | Wait, or reload |

## Signing in

| Condition | Cause | Resolution |
|-----------|-------|------------|
| `Access not granted for startpage.` | The account is valid but holds no scope for this site | Request the `startpage` scope |
| `/access` appears again after previous use | The session passed 30 days | Sign in again |
| Sign-in does not persist | The browser is blocking cookies for this site | Allow cookies for this site |
| `Too many attempts` | Five access code attempts were made within a minute | Wait one minute |
| Signed in on one device but not another | Sessions are held per browser and per installed app | Sign in on each |

## Camera

| Condition | Cause | Resolution |
|-----------|-------|------------|
| The camera is never requested | Camera monitoring is switched off for this site | None |
| No Recent Visitors tile | Same cause as above | None |

## Escalation

Conditions not resolved by the above should be reported to the site operator.
Include the URL, the browser, whether the page was installed, and the time the
condition occurred.

Service availability is published at https://status.akn.me.uk.

## Related

- [Using the page](using.md)
- [Commands](commands.md)
- [Widgets](widgets.md)
- [Privacy](privacy.md)
