---
sidebar_position: 7
title: Privacy
---

# Privacy

What the page stores, what it sends, and what can be turned off.

## Camera

Camera monitoring is switched off for this site. The camera is not opened, no
permission is requested, and the `/camera` command has no effect.

The description below applies only if the feature is switched back on.

| Property | Behaviour when enabled |
|----------|------------------------|
| Requirement | Signed in. The camera is never opened for a signed-out visitor |
| Permission | Requested by the browser on the first visit after it is enabled |
| Refusal | Monitoring stops. No message is shown |
| Trigger | A change of more than four percent of the picture between two checks |
| Check rate | Twice per second, paused while the tab is in the background |
| Capture rate | At most one capture every eight seconds |
| Face detection | Runs on the device. The picture is not sent for detection |
| Recognition | Compared against face signatures already held in this browser |
| Still images | A small image is uploaded when a face is found |
| Motion without a face | Uploaded after 30 seconds if no face appears in that time |
| Video clips | Ten seconds before and ten seconds after a face is found. Kept in this browser only |
| Clip retention | The 50 most recent. Older clips are deleted |
| Preview | Signed-in viewers see the images in the Recent Visitors tile with a label and time |
| Turning it off | `/camera`. The choice persists across visits |

Face signatures and video clips never leave the browser that recorded them.
Clearing the browser data for the site removes both.

## What is stored

| Held on the server | Held in this browser |
|--------------------|----------------------|
| Todos | Dim level |
| Timer sessions and their projects | Background brightness |
| Alarms | Camera preference |
| Habits and their daily marks | Face signatures |
| Search terms entered in the palette | Video clips |
| Photos | |
| Camera still images, when enabled | |

Projects, tasks, calendar entries and repository activity are held by the
services they come from, not by this page.

## What is sent

| Destination | Sent | When |
|-------------|------|------|
| Google | The search term | On searching, in a new tab |
| A location service | The network address | Once per visit, for the weather |
| A weather service | Approximate coordinates | Once per visit |
| Hacker News | Nothing beyond the request | On load and every 15 minutes |
| The aknThoughts board | Nothing beyond the request | On load and every 30 minutes |
| An AI service | Timer labels, outstanding todo text, project names | See [Assistant](assistant.md) |

Search terms are recorded against the account only while signed in. Searches
made while signed out are not recorded.

## What the user controls

| Control | Method | Persists |
|---------|--------|----------|
| Recording searches | Sign out. Searches are recorded only while signed in | Yes |
| Deleting a recorded search | Not available | |
| Camera monitoring | `/camera`, when the feature is switched on | Yes |
| Sending a timer label for matching | Do not use timers | |
| Sending todo text for matching | Do not select **✦** | |
| Weather location | Not available. Location is taken from the network address | |
| Browser notifications | Granted or refused in the browser | Yes |
| Ending the session | `/logout` | Immediate |

Signing out ends the session on this device and returns to `/access`.

## Visibility to others

| Item | Visible to a signed-out visitor |
|------|--------------------------------|
| Todos marked public | Yes |
| Timer sessions marked public | Yes |
| Photos marked public | Yes |
| Projects and tasks marked public | No. Nothing is shown while signed out |
| Alarms, habits, calendar, notifications | No |
| Camera images and clips | No |
| Search history | No |

Whether an item is public is set where the item is held, not from the page.

## Related

- [Assistant](assistant.md) covers what the AI feature receives.
- [Widgets](widgets.md) covers which tiles hold private data.
- [Diagnostics](diagnostics.md) covers permission conditions.
