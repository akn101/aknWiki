---
sidebar_position: 5
title: Diagnostics
---

# Diagnostics

Observed conditions and their resolutions.

## The map

| Condition | Cause | Resolution |
|-----------|-------|------------|
| Circles are grey everywhere | Live counts have not arrived yet | Wait a moment. Grey with a dash means the count is unknown, not that the dock is empty |
| Counts look out of date | Counts refresh when the map settles, not continuously | Move the map slightly, or reopen the app |
| The map opens on London rather than on you | Location permission was declined or has not been granted | Allow location in iOS Settings, then select the location button |
| The location button will not stay filled | Any movement of the map stops it following you | Select it again. This is deliberate |
| A docking station is missing | It opened after the bundled list was built | Settings, then **Update station list** |
| Docking stations appear as plain dots | The map is zoomed out | Zoom in. Circles and names return |
| A docking station never appears in the list | It was hidden by a swipe | There is no unhide control in this version. Reinstalling the app clears hidden stations |
| The panel will not drag past a certain height | Reached the expanded height | This is the maximum |

## Signing in

| Condition | Cause | Resolution |
|-----------|-------|------------|
| Email or password incorrect | The credentials are not those of a cycle hire account | Sign in on the operator's website first to confirm they work |
| The sign-in screen stays open after signing in | Fixed in the current version | Update the app |
| No text message arrives at sign-in | The operator sends it at the first hire, not at sign-in | Continue. The code is requested when you first select **Hire** |
| Signed out unexpectedly | The operator expired the token | Sign in again |

## Hiring

| Condition | Cause | Resolution |
|-----------|-------|------------|
| **Hire** returns a list of prices instead of a code | The account has no active access period | Buy one on the operator's website, then try again |
| The access period shows None but one was bought | The cached copy is stale | Pull down to refresh in Settings |
| A charge appeared that was not expected | E-bikes and journeys over the included time cost extra on every access period | Check the charge with the operator |
| The release code was lost | It stays as a banner at the top of the map | Reopen the app. The banner survives closing it |
| The release code did not work at the stand | Codes expire after around ten minutes | Start the hire again from the app |
| The code is right but the bike will not release | A dock or bike fault, outside the app | Try another docking point. Report the fault to the operator |
| No text message arrives before the first hire | The mobile number on the account is wrong or absent | Correct it on the operator's website |

## Account and journeys

| Condition | Cause | Resolution |
|-----------|-------|------------|
| Journey history is empty | The account has no completed journeys, or the cache has not been filled | Pull down to refresh |
| Details show an old value | Details are cached and shown with a last-updated time | Pull down to refresh |
| Password and security answer are not listed | They are deliberately withheld from display | Nothing to resolve |

## Escalation

| Subject | Where to raise it |
|---------|-------------------|
| A bike, a dock, a charge, an access period, or an account | The scheme operator |
| The app itself | [Support](support.md) |

Faults with bikes, docking points, charges, and accounts belong to the scheme
operator. akn cannot see, alter, or refund any of them.
