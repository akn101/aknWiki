---
sidebar_position: 1
title: Overview
---

# aknStartpage

| | |
|---|---|
| URL | https://startpage.akn.me.uk |
| Description | Browser start page with a command palette, personal widgets and a glanceable display mode |
| Access | Public read. Editing, private items and display mode require akn ID |
| Pricing | Free |

## Overview

aknStartpage allows users to replace the browser new tab with a single page
that runs commands from a keyboard palette, searches the web, and shows
personal information at a glance. Access controls are available and can be set
by the organisation using akn ID scopes.

Signed out, the page shows the clock, search, weather, quick links and items
marked public. Signing in adds editing, private items, alarms, habits,
calendar, notifications and display mode.

## Capabilities

| Capability | Availability |
|------------|--------------|
| Search the web from the palette | Any visitor |
| Open a quick link | Any visitor |
| Dim the screen and set background brightness | Any visitor |
| Run timers during a visit | Any visitor |
| Read public todos, timers and photos | Any visitor |
| Read the thoughts feed and Hacker News | Any visitor |
| Install as an app | Any visitor |
| Add, complete and clear todos | Signed in |
| Save a timer session | Signed in |
| Set alarms | Signed in |
| Track habits | Signed in |
| See the calendar, projects, GitHub and notifications | Signed in |
| Search suggestions from previous searches | Signed in |
| Full-screen display mode | Signed in |
| Add projects and tasks, change task status | akn ID administrators |
| Camera monitoring | Not available. Switched off for this site |
| Edit the quick links from the page | Not available |
| Reorder, hide or add widgets | Not available |
| Light theme | Not available |
| Keep a running timer across a reload | Not available |
| Ask the AI feature a question | Not available |

## Page sections

The page holds four full-height sections. Scrolling snaps to one at a time.

| Section | Contents |
|---------|----------|
| Landing | Clock and search |
| Dashboard | Clock, search, weather, todos, timers, alarms, quick links |
| Feed | This week, habits, projects, GitHub, Hacker News, calendar, photos, thoughts |
| Display | Rotating glanceable panels |

## Signing in

Two methods are offered at `/access`.

| Method | Detail |
|--------|--------|
| akn ID | Select **Login with akn ID**. Also available as `/login` in the palette |
| Access code | Enter the code in the field. Five attempts per minute |

An account qualifies by holding the `startpage` scope, the wildcard scope `*`,
or the administrator role. An account without one of these is refused with an
access message rather than returned to sign-in.

Sessions last 30 days.

## Next steps

- [Using the page](using.md) covers the palette, searching and moving around.
- [Commands](commands.md) lists every command.
- [Widgets](widgets.md) covers each tile and display mode.
- [Installing](installing.md) covers desktop and mobile installation.
- [Assistant](assistant.md) covers the AI matching feature.
- [Privacy](privacy.md) covers what is stored and what is sent.
- [Diagnostics](diagnostics.md) lists observed conditions and resolutions.

## Related products

- [aknID](../../platform/akn-id/overview.md), sign-in for personal widgets
- [aknThoughts](../../core/thoughts/overview.md), source of the thoughts feed
- [aknStatus](../../core/status/overview.md), availability of akn services
