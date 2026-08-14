---
sidebar_position: 3
title: Commands
---

# Commands

Commands are entered in the command palette and begin with `/`. Entering `/`
alone lists them.

## Reference

| Command | Effect | Before running |
|---------|--------|----------------|
| `/todo TEXT` | Adds the text to the todo list | Requires sign-in. Nothing is added when signed out and no message is shown |
| `/record LABEL` | Starts a timer with that label | The timer is lost on reload. Saving the finished session requires sign-in |
| `/record` | Lists running timers, each with elapsed time, so one can be stopped | Offers **Stop all** when more than one timer is running |
| `/alarm HH:MM` | Sets an alarm for that time | Requires sign-in. The time must be entered as digits, for example `/alarm 07:30` |
| `/alarm HH:MM LABEL` | Sets an alarm with a label | The label is optional and follows the time |
| `/dim` | Offers dim levels: **Off**, **25%**, **50%**, **75%**, **90%** | The chosen level persists across visits and overrides automatic night dimming |
| `/bright` | Offers background brightness: **Default (100%)**, **Brighter (140%)**, **Max (200%)** | Affects the animated background only. Persists across visits |
| `/display` | Opens full-screen display mode | Requires sign-in. Leaves the main page |
| `/clear` | Deletes every completed todo | Requires sign-in. There is no undo |
| `/login` | Starts akn ID sign-in | Offered only while signed out |
| `/logout` | Ends the session and returns to `/access` | Offered only while signed in |
| `/camera` | No effect | Listed in the palette, but camera monitoring is switched off for this site |

## Actions without a command

With the palette open and no text entered, the **Actions** group offers the
same operations. Selecting one enters its command so the remaining text can be
typed. The **Go to** group above it opens a quick link directly.

## Timers

`/record` starts a timer immediately. Timers run in parallel and each is listed
with its own elapsed time.

| Property | Detail |
|----------|--------|
| Parallel timers | Unlimited. Each is started and stopped separately |
| Elapsed time | Counts up every second while the page is open |
| Stopping | Saves the session and matches it to a project. See [Assistant](assistant.md) |
| Stop all | Stops every running timer and saves each one |
| Reload | Running timers are lost. Their time is not saved |
| Closing the tab | Same as a reload |

The same timers can be started and stopped from the **Timer** widget.

## Alarms

`/alarm` adds the alarm to the **Alarms** widget on the dashboard section.

| Property | Detail |
|----------|--------|
| Repetition | The alarm fires at that time every day until it is disabled or removed |
| Sound | A chime plays for about three seconds |
| Ringing state | The widget shows the label and clears when selected |
| Browser notification | Requested when the first alarm is set. Shown only if permission is granted |
| Requirement | The page must be open in a tab for the alarm to fire |
| Sound requirement | The page must have been selected or tapped at least once during the visit |

## Dimming and brightness

Two independent controls affect how bright the page is.

| Control | Affects | Persists |
|---------|---------|----------|
| `/dim` | An overlay across the whole page | Yes |
| `/bright` | The animated background only | Yes |

Setting any dim level, including **Off**, stops the automatic dimming that
otherwise applies between 22:00 and 06:00.

## Related

- [Using the page](using.md) covers opening the palette and searching.
- [Widgets](widgets.md) covers the todo, timer and alarm widgets.
- [Diagnostics](diagnostics.md) covers commands that appear to do nothing.
