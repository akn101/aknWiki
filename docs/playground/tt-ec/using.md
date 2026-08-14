---
sidebar_position: 2
title: Using the viewer
---

# Using the viewer

The viewer works in two stages. Save the timetable as an HTML file, then load
that file into the viewer.

A laptop is recommended for the first stage. Mobile browsers save pages in
formats the viewer cannot read.

## Saving the timetable file

1. Open the Eton student timetable portal and sign in with the Microsoft
   school account.
2. Wait for the full timetable to load.
3. Save the page using the browser save function, choosing the correct format.

| Browser | Shortcut | Format to select |
|---------|----------|------------------|
| Chrome | `Ctrl+S` or `Cmd+S` | Webpage, HTML only |
| Edge | `Ctrl+S` or `Cmd+S` | Webpage, HTML only |
| Firefox | `Ctrl+S` or `Cmd+S` | Webpage, HTML only |
| Safari | `Cmd+S` | Page Source |

Select HTML only, or Page Source in Safari. Web Archive and Complete Webpage
are not supported.

## Platform support

| Platform | Support | Detail |
|----------|---------|--------|
| Windows, using Chrome, Edge, or Firefox | Full | |
| macOS, using Chrome, Edge, or Firefox | Full | |
| macOS, using Safari | Full | Select Page Source when saving |
| iOS and iPadOS | Limited | Browsers save a Web Archive (`.webarchive`), which the viewer cannot read |
| Android | Limited | Chrome saves MHTML (`.mhtml`), which the viewer cannot read |

On iOS or Android, save the file on a laptop and transfer it to the device, or
use a browser that offers an HTML-only save.

## Loading the timetable

1. Open https://tt.ec.playground.akn.me.uk. The address opens the upload and
   documentation page.
2. Upload the saved HTML file.

The timetable is read from the file and the weekly view is displayed.

## Reading the week

The week is laid out by day and colour coded by subject or lesson type. Each
lesson shows its time, subject, teacher, and room.

| Item | Detail |
|------|--------|
| Teacher names | Abbreviated codes are replaced with full names where the name is known |
| Room | Room and location are shown against each lesson |
| Early Work | Lessons designated Early Work carry a visual indicator |
| School letter | The current week letter is detected and displayed |

## Weekly counts

| Statistic | Meaning |
|-----------|---------|
| Allocated lessons | Total timetabled lessons |
| Free periods | Free periods in the week |
| Subject count | Distinct subjects |
| Teacher count | Distinct teachers |

## Related

- [Overview](overview.md) covers capabilities and file handling.
- [Calendar export](calendar-export.md) covers exporting the timetable.
