---
sidebar_position: 5
title: Diagnostics
---

# Diagnostics

Observed conditions and their resolutions.

## Signing in

| Condition | Cause | Resolution |
|-----------|-------|------------|
| `Incorrect email or password` | The address and password do not match an account | Retry, or use another method. Password reset is not available |
| `No account with that email` | No account holds that address | Request access, or sign in with a method the account already holds |
| `Too many attempts` | Repeated failed attempts on the same account | Wait, then retry |
| Nothing happens after selecting a provider | The provider window was closed or blocked. No message is shown | Allow windows over the page, then retry |
| `Invalid phone number` | The number was entered without `+` and a country code | Re-enter as `+447700900000` |
| `Incorrect code` | The six digit code was mistyped or has expired | Request a new code |
| `That number is not linked to an account` | Phone sign-in only signs in a number already attached to an account | Sign in another way, attach the number from the account page, then retry |
| The code never arrives | The code was not sent. The failure is reported under the field | Select **Resend code**. Check the address is the one held on the account |
| `Something went wrong` | The sign-in was refused for a reason with no specific message | Retry, or use another method |

## Reaching a site

| Condition | Cause | Resolution |
|-----------|-------|------------|
| Sign-in succeeds, then returns to sign-in again, repeatedly | The account holds no scope for the site being entered. Sign-in itself is working | Request that site's scope. Signing in again will not change the outcome |
| **Pending Approval** shown on an account known to be approved | Same cause. The screen does not distinguish a missing scope from a missing approval | Request that site's scope |
| **Pending Approval** shows an empty address | The provider returned no verified email address, so the sign-in matched no existing account | Sign in with a method holding a verified address, then attach the other method from the account page |
| **Access Denied** | The account is set to rejected | Contact the site operator |
| `You don't have access to this app` | The account holds no scope for the application being entered | Request the scope named on the page |
| Sent to https://akn.me.uk rather than the intended site | Sign-in was opened directly rather than from the site | Start from the site's own address |
| The countdown finishes but the site asks to sign in again | The site keeps a session of its own and did not accept the return | Open the site's address again |
| A site stops accepting the account after 14 days | The session ended | Sign in again |

## Requesting access

| Condition | Cause | Resolution |
|-----------|-------|------------|
| `Please verify your email first` | **Send Request** was selected before a code was requested | Select **Send verification code**, then enter the code |
| An error appears after the code is accepted | The request was not recorded | Contact the site operator directly |
| No reply after a request | No notification is sent on any outcome | Sign in again to see whether the state has changed |

## Account page

| Condition | Cause | Resolution |
|-----------|-------|------------|
| The account page returns to the sign-in page | No signed-in account, or the session ended | Sign in |
| `That account is already linked to a different akn ID account` | The provider account is attached to another person | Sign in as that account, or ask an administrator to merge the two |
| `That number is already linked to a different akn ID account` | The number is attached to another person | Ask an administrator to move it |
| **Unlink** is not offered | Only one method remains attached, or the method cannot be detached | Attach a second method first. Phone numbers and passwords cannot be detached |
| Deletion refused, asking to sign in again | Deletion requires a recent sign-in | Sign out, sign in again, then repeat |
| Edits are lost | The form saves as a whole and only on **Save Changes** | Re-enter and save before leaving the page |

## Administration

| Condition | Cause | Resolution |
|-----------|-------|------------|
| `Access denied` at `/admin` | The account is not an administrator and holds no `*` scope | Request the role or the scope |
| Other akn sites remain reachable after signing out | Signing out from the account page does not end the shared session | Sign out from the administration area, or close the browser |
| A person appears twice in the people list | Two sign-in methods resolved separately because neither was attached to the other | Link the identities on one record, then remove the duplicate |
| A granted scope has no effect for the person | Their session predates the change | Have them sign out and sign in again |

## Address not found

`404 Page not found` indicates a mistyped address. **Go home** returns to the
sign-in page.

## Escalation

Conditions not resolved by the above should be reported to the site operator.
Include the address, the sign-in method used, the browser, and the time.

Service availability is published at https://status.akn.me.uk.

## Related

- [Overview](overview.md)
- [Signing in](signing-in.md)
- [Scopes and access](scopes.md)
- [Your account](account.md)
