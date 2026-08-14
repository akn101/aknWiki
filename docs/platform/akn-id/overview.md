---
sidebar_position: 1
title: Overview
---

# aknID

| | |
|---|---|
| URL | https://id.akn.me.uk |
| Description | Single sign-in for the akn sites, with per-site access control |
| Access | Anyone can sign in. Reaching a site requires an approved account holding that site's scope |
| Pricing | Free |

## Overview

aknID allows users to sign in once and reach every akn site their account has
been granted. Approval and per-site access controls are available and can be
set by the organisation using scopes.

An account represents a person rather than a sign-in method. Several sign-in
methods attach to one account, and any of them signs the same person in.

## Capabilities

| Capability | Availability |
|------------|--------------|
| Sign in with a password, a provider account, a phone number, or an emailed code | Any visitor |
| Return automatically to the site that asked for sign-in | Any signed-in account |
| Reach an akn site | Approved accounts holding that site's scope |
| View account status and granted scopes | Any signed-in account |
| Edit profile, contact, social, and preference details | Any signed-in account |
| Attach or remove sign-in methods | Any signed-in account |
| Delete the account | Any signed-in account |
| Approve, reject, and grant scopes to other people | Administrators |
| Create an account from the sign-in page | Not available. Access is by request |
| Reset a forgotten password | Not available |
| Change the email address on the account | Not available. The field is read only |
| Remove a phone number or password once attached | Not available |
| Attach GitHub or Steam after sign-in | Not available |
| Notification when access is granted or refused | Not available |

## Account states

Every account holds one state. The state decides what the sign-in page shows
once the account has been identified.

| State | Sign-in outcome |
|-------|-----------------|
| Pending | **Pending Approval**. No site can be reached |
| Approved | Sent on to the requested site, if the account holds a scope for it |
| Rejected | **Access Denied**. No site can be reached |

Approval alone does not admit an account to a site. See [Scopes and access](scopes.md).

## Next steps

- [Signing in](signing-in.md) covers the methods, the return to the originating site, and signing out.
- [Scopes and access](scopes.md) covers the access model and how access is requested and granted.
- [Your account](account.md) covers profile details and sign-in methods.
- [Diagnostics](diagnostics.md) lists observed conditions and resolutions.

## Related products

- [aknAPI](../../platform/akn-api/overview.md), verifies sessions issued here
- [aknStartpage](../../core/startpage/overview.md), restricted by scope
- [aknThoughts](../../core/thoughts/overview.md), restricted by scope
- [aknStatus](../../core/status/overview.md), restricted by scope
