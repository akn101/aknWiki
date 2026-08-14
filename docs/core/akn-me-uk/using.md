---
sidebar_position: 2
title: Using the site
---

# Using the site

Every section is open to any visitor. No account is required to move around the
site.

## Arrival

https://akn.me.uk opens the entry screen at `/start`.

| Property | Detail |
|----------|--------|
| Headline | `Strive for excellence.` |
| Progress line | Fills across the bottom of the screen over five seconds |
| Automatic advance | Home opens when the line completes |
| Manual advance | Select anywhere on the screen |
| Navigation controls | None. The menu and the command palette are absent here |

The entry screen is reachable afterwards from **strive for excellence** at the
foot of the side menu.

## The menu

The menu button is present on every section except the entry screen.

| Window width | Position | Behaviour |
|--------------|----------|-----------|
| Above 768 pixels | Left edge, vertically centred | Retracts against the edge and slides out under the pointer |
| 768 pixels and under | Bottom centre | Fixed in place |

Selecting the button opens the menu from the left.

| Group | Entries |
|-------|---------|
| Search | **Search…**, which opens the command palette |
| Pages | **Home**, **Work**, **Flair**, **Photography**, **Letters** |
| Secondary | **About**, **Contact** |
| External | **GitHub**, **Instagram** |
| Footer | Copyright line and **strive for excellence** |

The external group is omitted on narrow windows and on windows under 600 pixels
tall.

Any of the following closes the menu.

| Action | |
|--------|--|
| Press `Escape` | |
| Click outside the menu | |
| Select the close control shown on narrow windows | |

## The header

A header is fixed to the top of About, Work, Flair, Photography, and Contact.
Home, Letters, and individual letters carry no header.

| Control | Effect |
|---------|--------|
| Section title | Label only |
| Lock button | Opens the access code dialog |
| Theme button | Switches between light and dark |

The header is transparent at the top of a section and becomes opaque as the
section is scrolled.

## Command palette

The palette searches sections, projects, and experiments, and opens external
links.

| Method | Available on |
|--------|--------------|
| `Cmd`+`K` or `Ctrl`+`K` | Every section except the entry screen |
| **Search…** | Side menu |
| **⌘K** | Home footer |

Pressing the shortcut again closes the palette. `Escape`, a click outside the
panel, and selecting an entry all close it as well.

Typing filters every group at once. With no match the panel shows `No results`.

### Commands

| Group | Entry | Effect |
|-------|-------|--------|
| Pages | **Home** | Opens the entry screen, which then advances to Home |
| Pages | **About**, **Work**, **Flair**, **Photography**, **Letters**, **Contact** | Opens that section |
| Projects | One entry per project | Opens the project in a new tab. Entries carrying no link open Work |
| Flair | One entry per experiment | Opens Flair. Each entry shows its month and year |
| Links | **GitHub** | Opens the profile in a new tab |
| Links | **Instagram** | Opens the profile in a new tab |
| Links | **Email** | Opens the device's mail application |

Projects and experiments withheld from the current visitor are absent from
these groups.

### Access command

Typing `/access` switches the palette into access mode and hides the other
groups.

| Input | Row shown | Effect |
|-------|-----------|--------|
| `/access` with fewer than five digits | `/access <5-digit code>` | None |
| `/access` followed by five digits | **Unlock with code** | Submits the code |

A confirmation reads `Access granted` or `Invalid access code`.

## Theme

| Property | Detail |
|----------|--------|
| Default | Follows the device colour scheme |
| Manual control | Theme button in the header |
| Availability of the control | Present only when the device reports a dark colour scheme |
| Sections without the control | Entry screen, Home, Letters, individual letters |

## Loading indicator

A `Loading…` indicator appears at the bottom centre when a section takes longer
than about half a second to open. It clears when the section opens, and after
seven seconds in any case.

## Related

- [Sections](sections.md) covers what each section contains.
- [Protected content](protected-content.md) covers the lock button and the access dialog.
- [Diagnostics](diagnostics.md) covers conditions encountered while navigating.
