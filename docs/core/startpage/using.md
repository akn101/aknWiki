---
sidebar_position: 2
title: Using the page
---

# Using the page

The command palette is the primary control. Everything typed goes to it:
searches, addresses and commands.

## Opening the palette

| Action | Result |
|--------|--------|
| Press `⌘K` on macOS, `Ctrl+K` elsewhere | Opens the palette. Press again to close |
| Type any single character | Opens the palette with that character already entered |
| Select the search bar | Opens the palette empty |
| Select the **⌘** button at the bottom right | Opens the palette empty |

Typing to open works only when no field is focused.

### Closing

| Action | |
|--------|--|
| Press `Escape` | |
| Select outside the palette | |

The entered text is discarded on close.

## Searching

1. Open the palette.
2. Enter the search term.
3. Press `Enter`.

Results open in a new tab. The current page stays where it is.

| Entered text | Offered action |
|--------------|----------------|
| Words or a phrase | **Search Google for** the phrase |
| A domain such as `example.com` | **Go to** the address, opened directly |
| A full web address | **Go to** the address, opened directly |
| Text beginning with `/` | The matching command |

Text containing a space is always treated as a search.

### Suggestions

Previous searches appear below the search action, up to five, most recent
first, filtered to what has been entered. Suggestions are recorded and shown
only while signed in. Repeated searches are listed once.

There is no way to delete a recorded search from the page.

## Navigating results

| Key | Action |
|-----|--------|
| `Down arrow` | Move down. The selection wraps to the top |
| `Up arrow` | Move up. The selection wraps to the bottom |
| `Enter` | Run the selected result |
| `Escape` | Close |

Results are grouped. With no text entered, the palette lists **Go to** for
quick links and **Actions** for commands. Selecting an action enters its
command rather than running it, so the remaining text can be typed.

Entering `/` alone lists every command.

## Quick links

Eight links are fixed and open in a new tab.

| GitHub | Gmail | YouTube | Claude |
|--------|-------|---------|--------|
| Linear | Notion | Twitter | Reddit |

The same links appear as a grid on the dashboard section and under **Go to** in
the palette. The list cannot be changed from the page.

## Moving around

Scrolling snaps to one section at a time. Past the first screen a small clock
appears at the top of the window.

## Automatic behaviour

| Behaviour | Timing |
|-----------|--------|
| Widgets refresh their data | Every 30 minutes |
| The page scrolls back to the first section | After 1 minute without input |
| Display mode opens over the page | After 10 minutes without input, between 09:00 and 18:00 |
| The screen dims | Between 22:00 and 06:00, unless a dim level has been set with `/dim` |
| A new version is loaded | Checked every 30 minutes, applied after 10 minutes without input |

Moving the mouse or pressing `Escape` closes the display overlay.

## Signing in

1. Open the palette and enter `/login`.
2. Select **Login with akn ID**.
3. Complete sign-in.

The page returns to the first section once signed in. An access code field is
also available at `/access`.

To sign out, enter `/logout` and select **Log out**. The session ends
immediately and the browser returns to `/access`.

## Related

- [Commands](commands.md) lists every command and its requirements.
- [Widgets](widgets.md) covers what each tile shows.
- [Diagnostics](diagnostics.md) covers conditions encountered while searching.
