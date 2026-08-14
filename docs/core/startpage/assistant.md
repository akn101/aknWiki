---
sidebar_position: 6
title: Assistant
---

# Assistant

One AI feature is present. It sorts work into projects. It answers no
questions, holds no conversation, and has no input of its own.

## What it does

| Feature | Trigger | Result |
|---------|---------|--------|
| Timer matching | Stopping a timer | The saved session is filed against one of the projects |
| Todo matching | Selecting **✦** on the Todos widget | Each outstanding todo is proposed for a project |

Both require sign-in. Both match only against projects that already exist.

## Timer matching

Matching runs automatically when a timer stops. The label entered when the
timer started is compared against the project list, and the session is filed
against the closest project.

| Condition | Result |
|-----------|--------|
| The label clearly belongs to a project | The session is filed against it |
| Nothing fits | The session is saved with no project |
| Matching is unavailable | The session is saved with no project |
| A project name is returned that does not exist | Discarded. The session is saved with no project |

The result is not shown when the timer stops. It appears in the time logged on
the project card and in the This week tile, where unmatched time is counted
separately as not matched to a project.

There is no way to correct a match from the page.

## Todo matching

1. Select **✦** in the header of the Todos widget.
2. Wait for the proposals.
3. Review the list. Each todo shows a project or `no match`.
4. Select **Move N** to apply, or **Cancel** to discard.

| Property | Detail |
|----------|--------|
| Scope | Outstanding todos only. Completed todos are ignored |
| Proposals | One project or `no match` per todo |
| Applying | Creates a task in each matched project and deletes the todo |
| Unmatched todos | Left in the todo list, untouched |
| Undo | Not available. The todo is deleted once moved |
| Editing a proposal | Not available. Either apply the set or cancel |

**✦** appears only while signed in and only when at least one outstanding todo
exists.

## What leaves the device

| Sent | Not sent |
|------|----------|
| The label entered for a timer | Todo text that is already completed |
| The text of outstanding todos, when **✦** is selected | Alarms, habits and calendar entries |
| The names of the projects | Photos and camera images |
| | Search history |
| | Any account detail |

Processing takes place in the European Union. Nothing is sent unless a timer is
stopped or **✦** is selected.

## Limits

| Limit | Detail |
|-------|--------|
| Free-form questions | Not available. There is no prompt to type into |
| Summaries, drafting, chat | Not available |
| New projects | Never created. Matching only uses projects that exist |
| Accuracy | Proposals can be wrong. Review before selecting **Move** |
| Failure | Silent. A failed match saves the session with no project |
| Correction | Not available from the page once applied |

## Related

- [Widgets](widgets.md) covers the Todos widget and the project cards.
- [Commands](commands.md) covers starting and stopping timers.
- [Privacy](privacy.md) covers everything else the page sends and stores.
