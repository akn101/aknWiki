---
sidebar_position: 1
title: Overview
---

# Dockside

| | |
|---|---|
| Platform | iPhone. iOS 17 or later |
| Description | Map of every docking station in London's public cycle hire scheme, with live availability and bike release |
| Access | The map is open to everyone. Hiring requires a cycle hire account held with the scheme operator |
| Pricing | Free. The app charges nothing and takes no commission |
| Coverage | London only |

## Overview

Dockside allows anyone to see every docking station in London, how many bikes
and spaces each one holds, and how far away it is. No account is needed for
any of that.

Hiring a bike additionally requires an account with the operator of the cycle
hire scheme and an active access period. Dockside does not create accounts,
does not sell access periods, and never handles payment details. Those happen
on the operator's own website.

Dockside is an independent app. It is not published by, endorsed by, or
affiliated with the operator of the scheme or with Transport for London.

## Capabilities

| Capability | Availability |
|------------|--------------|
| See every docking station on a map | Any user |
| See live bike, e-bike, and space counts | Any user |
| See distance to a docking station | Any user, with location permission |
| Search docking stations by name | Any user |
| Pin a docking station | Any user |
| Hide a docking station | Any user |
| Release a bike | Signed in, with an active access period |
| Read journey history | Signed in |
| See the access period held on the account | Signed in |
| Buy or renew an access period | Not in the app. Opens the operator's website |
| Change payment details | Not in the app. Opens the operator's website |
| Create a cycle hire account | Not in the app. Opens the operator's website |
| Reserve a bike in advance | Not available. The scheme does not offer it |
| Plan a route between two docks | Not available |
| Use the app outside London | Not available. The scheme is London only |
| Use the app on iPad | Not available. iPhone only |
| Use the app in landscape | Not available. Portrait only |
| Read the app in a language other than English | Not available |

## Where the data comes from

| Data | Source | How often it updates |
|------|--------|----------------------|
| Docking station locations and names | Transport for London Unified API, published as open data | Bundled with the app. Refreshed at most weekly, in the background |
| Bike, e-bike, and space counts | Transport for London Unified API | On opening the map, then as the map is moved |
| Account details, access period, journey history | The cycle hire scheme operator | On opening the relevant tab. Cached between launches |
| Bike release codes | The cycle hire scheme operator | At the moment of hire |

Dockside runs no server. Nothing a user does in the app is reported to akn.

## Attribution

Powered by TfL Open Data. Contains OS data © Crown copyright and database
rights 2016 and Geomni UK Map data © and database rights 2019.

## Next steps

- [Using the app](using.md) covers the map, searching, pinning, and hiding.
- [Hiring a bike](hiring.md) covers signing in, access periods, and release codes.
- [Your information](privacy.md) covers what the app stores and what it sends.
- [Diagnostics](diagnostics.md) lists observed conditions and resolutions.
- [Support](support.md) covers how to report a problem.
