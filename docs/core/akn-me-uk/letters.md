---
sidebar_position: 5
title: Letters
---

# Letters

Letters holds written pieces. Any visitor can read the open ones. Restricted
pieces require an access code or an akn ID sign-in.

## The list

The list sits at `/letters`. Each row carries the title, the year of
publication, and a one line excerpt.

| Property | Detail |
|----------|--------|
| Ordering | Fixed. Not visitor-controllable |
| Search | Not available |
| Filtering | Not available |
| Pagination | None. The full list loads at once |
| Empty state | `No posts yet. Check back soon!` |
| Access control | Lock button beside the heading |

Letters carries no section header, so it carries no theme control. The menu
button and the command palette remain available.

## Restriction levels

| Level | Appears in the list | Text |
|-------|--------------------|------|
| Open | Yes | Shown |
| Limited | Yes | Withheld until access is granted |
| Unlisted | Yes | Withheld until access is granted |
| Restricted | Only once access is granted | Withheld until access is granted |

## Reading a letter

Selecting a title opens the piece.

| Element | Detail |
|---------|--------|
| Title | Shown |
| Publication date | Shown |
| Reading time | Shown where the piece carries one |
| Tags | Shown as pills. Any restriction tag appears among them |
| Feature image | Shown where the piece carries one, with its caption |
| Contents | Sidebar built from the headings. Wide windows only. The current heading is highlighted while scrolling |
| Author credit | Shown only where someone other than Ahnaf Kabir is credited |
| Return | **Back to letters** |

Selecting an entry in the Contents sidebar scrolls to that heading.

## Opening a restricted letter

1. Select the title in the list, or open the link directly.
2. The page reads `This letter is restricted. Please enter the access code to
   view.` and the access dialog opens.
3. Enter the five digit code, or select **Login with akn ID**.
4. The text loads in place.

Closing the dialog without entering a code leaves the message on screen. The
dialog does not reopen from that screen. Return to the list and select the
letter again.

## Capabilities

| Capability | Availability |
|------------|--------------|
| Read open letters | Any visitor |
| Read limited, unlisted, and restricted letters | Access holders |
| Jump between headings | Wide windows, where the piece carries headings |
| Search or filter the list | Not available |
| Sort the list | Not available |
| Comment or react | Not available |
| Subscribe to new letters | Not available |
| See how many letters are withheld | Not available |

## Related

- [Protected content](protected-content.md) covers access codes and akn ID sign-in.
- [Using the site](using.md) covers reaching Letters from the menu and the command palette.
- [Diagnostics](diagnostics.md) covers conditions encountered while reading.
