---
sidebar_position: 3
title: Motion and display
---

# Motion and display

The site animates on arrival and while scrolling. Motion follows the operating
system's reduced motion setting.

## The opening animation

On first arrival the AKN mark assembles over the whole window, a short phrase
appears, and the page is then revealed. Scrolling is locked while it runs.

| Property | Detail |
|----------|--------|
| Duration | Three to four seconds |
| Variant | One of two, chosen at random |
| Phrase | One of seven, chosen at random |
| Repeat | Once per browsing session |
| Skip control | Not available |

Opening the site in a new tab or after closing the browser plays the animation
again.

### Playing it again

Add `?intro=` to the address.

| Address | Result |
|---------|--------|
| `https://akn.org.uk/?intro=` | A variant chosen at random |
| `https://akn.org.uk/?intro=split` | The draw and split variant |
| `https://akn.org.uk/?intro=pop` | The pop out variant |

The address returns to `https://akn.org.uk` once the animation starts.

## Reduced motion

Setting the operating system to reduce motion changes the following.

| Element | Behaviour |
|---------|-----------|
| Opening animation | Does not play, including when `?intro=` is present |
| Name band | Held still |
| Section entrance animations | Not applied. Content is present on arrival |
| Hero artwork | Drawn once and held still |
| Border highlight under the pointer | Off |

## Hero artwork

The artwork beside the opening headline is drawn live and moves continuously.
It pauses while scrolled out of view.

### Tuner panel

Three clicks anywhere on the page within half a second open a panel titled
**Ferrofluid**.

| Control | Effect |
|---------|--------|
| **Pixel size** | Size of each block in the grid |
| **Ball count** | Number of shapes |
| **Speed** | Limit on how fast the shapes travel |
| **Randomness** | How much the shapes wander |
| **Threshold** | How much of each shape is drawn |
| **Min radius** | Smallest shape size |
| **Max radius** | Largest shape size |
| **Reset** | Restores every control to its default |

Drag the panel by its title bar to move it. Close it with **✕**, or with
another three clicks. Values are not retained. Reloading restores the defaults.

## Pointer highlight

On windows wider than 900 pixels, and with a mouse or trackpad, the borders of
the product cards and the four work areas light up near the pointer. Touch
input and narrower windows do not show it.

## Related

- [Using the site](using.md) covers navigation and contact.
- [Diagnostics](diagnostics.md) covers conditions related to motion.
