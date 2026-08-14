---
sidebar_position: 3
title: Sections
---

# Sections

Six sections hold general content. Letters is covered on its own page.

## Home

Home sits at `/home`. It carries a status strip, an introduction, and the most
recent experiment.

### Status strip

| Element | Detail |
|---------|--------|
| Clock | Runs in the timezone of the last known location, to the second |
| Location | Last known location. Reads `Location unavailable` when none is held |
| Stale location | Reads `last seen in <place>` when the reading is too old to stand as current |
| Previous visit | Reads `last visit from <place>` when a previous visit is recognised for this browser |
| Commissions | Reads `open to commissions` or `not taking commissions` |

While the strip is still resolving, a placeholder bar occupies its position.

### Location panel

The location label opens a panel headed `LOCATOR`.

| Window | How the panel opens |
|--------|--------------------|
| Wide | Hover over the location label |
| Narrow | Select the location label |

| Panel row | Detail |
|-----------|--------|
| Last Known Location | The current reading |
| Past Locations | Up to three, most recent first, one row per place |
| Future Locations | Up to six. Unconfirmed entries are italicised and marked `(tentative)` |

Empty states read `No recent Dawarich locations` and `No upcoming locations
listed`.

### Body and footer

The centre of the screen holds three lines of introduction and a card showing
the most recent experiment. The footer holds the contact address, `github`,
`instagram`, and `⌘K`.

Selecting the address copies it and the label changes to `copied!` for two
seconds.

## Work

Work sits at `/work` and lists projects newest first.

| Tab | Shows |
|-----|-------|
| **All** | Every project |
| **Active** | Projects with no end year, or an end year of 2025 or later |
| **Past** | Projects that ended before 2025 |

| Entry element | Detail |
|---------------|--------|
| Name | Opens the project in a new tab where the entry carries a link |
| Description | One line |
| Year | End year, or start year where the project is ongoing |
| Green dot | Marks an active project |

The empty state reads `Nothing here.`

## Flair

Flair sits at `/flair` and holds experiments in a masonry grid, newest first.

| Type | Presentation |
|------|--------------|
| Code | Runs live inside its card |
| Music | Waveform with a play control |
| Video | Plays inside the card |
| Image | Still image |

| Card element | Detail |
|--------------|--------|
| Title | Always shown |
| Date | Month and year |
| Description | Shown where the entry carries one |
| **Visit** | Shown where the entry carries a destination |

| Window width | Columns |
|--------------|---------|
| Under 500 pixels | 1 |
| 500 to 800 pixels | 2 |
| Above 800 pixels | 3 |

## Photography

Photography sits at `/photography`.

| Property | Detail |
|----------|--------|
| Layout | Masonry grid, 2 to 4 columns by window width |
| Loading | Each photograph appears blurred, then sharpens once it has downloaded |
| Full size | Select a photograph. It opens over the grid |
| Closing | Select the close control |
| Ordering | Fixed. Not visitor-controllable |
| Captions and titles | Not available |
| Download control | Not available |

## About

About sits at `/about` and carries a portrait, a biography, a **Currently**
list, and a signature. The **Currently** list holds three rows: Building,
Studying, and Listening.

## Contact

Contact sits at `/contact`.

| Element | Detail |
|---------|--------|
| Address | Shown in full. Select **copy** to copy it. The label reads `copied` for two seconds |
| Message box | Free text |
| **open in mail →** | Hands the text to the device's mail application with the subject prefilled |
| **Elsewhere** | GitHub, Instagram, and Thoughts |

The site does not send the message. **open in mail →** stays disabled until
text is entered, and the message is not retained after the mail application
opens.

## Related

- [Using the site](using.md) covers moving between these sections.
- [Letters](letters.md) covers the writing section.
- [Protected content](protected-content.md) covers entries withheld from Work and Flair.
