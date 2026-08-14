---
sidebar_position: 4
title: Widgets and panels
---

# Widgets and panels

Widgets occupy the dashboard and feed sections. Display mode presents the same
information as rotating full-screen panels.

## Dashboard widgets

| Widget | Shows | Signed out |
|--------|-------|------------|
| Clock | Time to the second, day and date | Full |
| Weather | Temperature, condition, wind speed and city | Full |
| Todos | Outstanding tasks, completed ones at the bottom | Public tasks only, read-only |
| Timer | Running timers and the last five saved sessions | Timers run. Sessions are not saved |
| Alarms | Alarms with times and labels | Shows `Log in to manage alarms` |
| Quick links | Eight fixed links | Full |

Weather is read once per visit and does not refresh. Location is approximate
and taken from the network address. If it cannot be determined, London is used.

### Todos

| Action | Detail |
|--------|--------|
| Add | Select **+**, enter the text, press `Enter`. Also available as `/todo` |
| Complete | Select the task. Completed tasks move to the bottom |
| Clear completed | Enter `/clear`. There is no undo |
| Reorder | Not available |
| Edit the text | Not available |

Adding, completing and clearing all require sign-in.

## Feed tiles

| Tile | Shows | Refresh |
|------|-------|---------|
| This week | Hours logged per life area since Monday, as bars | Every 30 minutes |
| Habits | A tick for today, the last seven days as dots, and the current streak | Every 30 minutes |
| Projects | Active projects, least time logged first, with their open tasks | Every 30 minutes |
| GitHub | Open pull requests, requested reviews, assigned issues, recent repositories, contribution grid | Every 30 minutes |
| Hacker News | The top eight stories with points, comments, source and age | Every 15 minutes |
| Calendar | Events for the next seven days, grouped by day | Every 15 minutes |
| Photos | One photo at a time with its caption | Once per visit |
| Thoughts | Notes published on the aknThoughts board | Every 30 minutes |

This week, Habits, Projects, GitHub and Calendar are empty while signed out. No
message distinguishes an empty tile from one that requires sign-in.

### Habits

| Action | Detail |
|--------|--------|
| Add | Select **+**, enter a name, press `Enter` |
| Mark today | Select the circle. Selecting again removes the mark |
| Delete | Select **✕**. There is no undo |
| Streak | Counts consecutive days. Today counts until the end of the day even before it is marked |

### Projects

Projects are listed with the least time logged this week first. Each card shows
its category, time logged this week, tasks in progress, and up to three
outstanding tasks.

| Action | Detail |
|--------|--------|
| Add a project | Select **+**, enter a name, choose a category and colour |
| Add a task | Select **add task** on the project card |
| Advance a task | Select the status dot. Todo, then In Progress, then Done |
| Move a task back | Hold `Shift` and select the status dot |
| Open in full | Select the project or task name. Opens in a new tab |

Adding and changing require an administrator account. A signed-in account
without administration sees the change on screen, and it is lost on the next
refresh.

Completed tasks disappear from the card after about one second.

### Photos

| Action | Detail |
|--------|--------|
| Advance | Automatic every 30 seconds |
| Move manually | Select **‹** or **›** |
| Add or remove | Not available from the page |

Only photos marked public are shown while signed out.

## Display mode

Display mode presents six panels in rotation on a plain background. It opens
automatically after 10 minutes without input between 09:00 and 18:00, from the
fourth page section, or with the `/display` command.

| Panel | Shows | Duration |
|-------|-------|----------|
| Glance | Time, weather, next event, next alarm | 25 seconds |
| Morning Brief | Time, date, weather, upcoming events, task and alarm counts | 28 seconds |
| Dashboard | Tasks and productivity | 22 seconds |
| Dev | Projects and GitHub activity | 22 seconds |
| Hacker News | Current top stories | 25 seconds |
| Focus | Time, date and a quote | 15 seconds |

| Control | Action |
|---------|--------|
| Point at the panel | Pauses the rotation until the pointer leaves |
| `Right arrow` | Next panel |
| `Left arrow` | Previous panel |
| Select a dot | Jumps to that panel |
| `Escape` | Closes the overlay. Does not apply to the full page at `/display` |
| Move the mouse | Closes the overlay |

The full page at `/display` requires sign-in. The fourth section of the main
page shows the same panels to any visitor, with signed-out data.

## Notifications

Messages sent to the page appear as a stack of toasts at the corner, each
labelled with its source. A toast clears after five seconds or when **✕** is
selected. Notifications are shown only while signed in and are checked every
eight seconds.

## Related

- [Commands](commands.md) covers the todo, timer and alarm commands.
- [Assistant](assistant.md) covers how timers and todos reach projects.
- [Diagnostics](diagnostics.md) covers empty and stale tiles.
