---
sidebar_position: 4
title: Your account
---

# Your account

The account page is available at `/account`, and at `/profile`, `/me`, and
`/settings`. It requires a signed-in account, and returns to the sign-in page
without one.

## Access

The first section states the account's position.

| Item | Detail |
|------|--------|
| Status badge | Pending or approved |
| Projects | The scopes the account holds. Reads `No projects assigned` when it holds none |
| **Admin Panel** | Shown to administrators only |

Neither the status nor the scopes can be changed from this page. See
[Scopes and access](scopes.md).

## Profile

| Section | Fields |
|---------|--------|
| Profile | Display Name, Username / Handle, Bio, Location, Website, Date of Birth, Occupation |
| Contact | Email, Phone |
| Social | Twitter / X, Instagram, GitHub, LinkedIn |
| Preferences | Language, Timezone |

Language offers English, Urdu, French, and Arabic. Timezone is filled from the
browser on first load.

Email is read only. Changing the address on an account is not available.

Select **Save Changes** to apply the whole form. The confirmation clears after
three seconds. Fields are not saved individually and leaving the page discards
unsaved edits.

## Sign-in methods

The **Sign-in Methods** section lists each method and whether it is attached.
Attaching a method from a signed-in session keeps one person on one account.
Signing in with a method that has never been attached creates a separate
account instead.

| Method | Attach | Detach |
|--------|--------|--------|
| Google | **Link** | **Unlink** |
| Apple | **Link** | **Unlink** |
| LinkedIn | **Link** | **Unlink** |
| Email / Password | Not available | Not available |
| Phone Number | **Link** | Not available |
| GitHub | Not available | Not available |
| Steam | Not available | Not available |

**Unlink** is offered only while more than one method remains attached.

### Attaching a phone number

1. Select **Link** on **Phone Number**.
2. Enter the number in full international format, for example `+447700900000`.
3. Enter the six digit code sent to the number.

The number is rejected before any message is sent unless it starts with `+`
and a country code. Once attached, signing in with that number reaches this
account.

### Attaching a provider account

Select **Link** on the method. A window opens over the page, or the page leaves
and returns if the window is blocked. A provider account already attached
elsewhere is refused, naming the conflict.

## Deleting the account

**Delete Account** sits at the foot of the page. It asks for confirmation, then
removes the account permanently. There is no recovery path.

Deletion requires a recent sign-in. Where it is refused, sign out, sign in
again, and repeat.

## Related

- [Signing in](signing-in.md) covers session length and signing out.
- [Scopes and access](scopes.md) covers how scopes are granted.
- [Diagnostics](diagnostics.md) covers conditions encountered on this page.
