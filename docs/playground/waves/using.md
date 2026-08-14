---
sidebar_position: 2
title: Using Waves
---

# Using Waves

Playback and visualisation start together. No account is required.

## Loading audio

1. Open https://waves.playground.akn.me.uk.
2. Add an audio file by dragging it onto the page or by using the file picker.
3. Select **Play**.
4. Adjust the pattern and parameters in the control panel.

Accepted formats are MP3, WAV, and OGG.

## Playback controls

| Control | Function |
|---------|----------|
| **Play / Pause** | Starts or pauses the audio and the animation together |
| **Stop** | Stops playback and returns the position to the start |
| Progress bar | Scrubs to any point in the audio |

## Wave patterns

| Pattern | Behaviour |
|---------|-----------|
| **Horizontal** | The wave travels left to right across the grid |
| **Vertical** | The wave travels top to bottom |
| **Diagonal** | The wave travels diagonally across the canvas |
| **Radial** | The wave spreads outward from a central point |
| **Spiral** | The wave follows a spiral path from the centre |
| **Ripple** | Circular ripples spread from one fixed source |
| **Random Ripples** | Several ripple sources run at once from random positions |
| **Sine** | A sine wave with a configurable direction |

## Settings

The control panel collapses out of the way and is grouped into sections.

### Grid

| Parameter | Effect |
|-----------|--------|
| **Grid Size** | Density of the dot grid. More dots give a finer grain |
| **Dot Radius** | Base size of each dot |
| **Scale Effect** | How far dot size changes with the wave |
| **Spacing** | Distance between dots |

### Wave

| Parameter | Effect |
|-----------|--------|
| **Amplitude** | Height and intensity of the wave |
| **Frequency** | Number of wave cycles across the canvas |
| **Speed** | Animation speed of the wave |
| **Direction** | Angle of travel, 0 to 360 degrees |
| **Position Displacement** | Offset of the wave origin |

### Radial and ripple patterns

| Parameter | Effect |
|-----------|--------|
| **Center X / Center Y** | Position of the radial origin on the canvas |
| **Ripple Source Count** | Number of simultaneous ripple origins in **Random Ripples** |

### Audio reactivity

| Parameter | Effect |
|-----------|--------|
| **Modulate** | Selects what the audio drives: amplitude, frequency, or speed |
| **Sensitivity** | How strongly the audio signal affects the selected parameter |
| **Smoothing** | How quickly the visualiser responds to sudden changes in the audio |
| **Frequency Band** | Selects the part of the spectrum that drives the effect: **Bass** or **Treble** |

## Colour

Dot colour follows audio intensity. Quiet passages render in blue tones and
loud peaks render in purple tones.

## Layout

| Region | Content |
|--------|---------|
| Header | The title, Resonance |
| Main canvas | The full-screen dot grid |
| Control panel | Collapsible sidebar holding every parameter |
| Footer | Attribution |

## Exporting

| Format | Result |
|--------|--------|
| PNG | A still image of the current frame |
| GIF | A three-second animation |
| WebM | A three-second video recording |

Exports capture the visualisation as it appears on screen, including the
current settings and audio position.

## Related

- [Overview](overview.md) covers capabilities and audio handling.
