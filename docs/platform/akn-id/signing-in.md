---
sidebar_position: 2
title: Signing in
---

# Signing in

Sign-in takes place at https://id.akn.me.uk. Sites that require an account send
visitors here and are returned to once sign-in completes.

The addresses `/login`, `/signin`, `/sign-in`, `/signup`, `/sign-up`,
`/register`, and `/logout` all lead to the sign-in page.

## Methods

The sign-in card offers the following.

| Method | Requirement |
|--------|-------------|
| Email and password | An email address and password already held on the account |
| **Continue with Google** | A Google account |
| **Continue with Apple** | An Apple account |
| **Continue with LinkedIn** | A LinkedIn account |
| **Continue with GitHub** | A GitHub account |
| **Continue with Steam** | A Steam account |
| **Phone Number** | A number already attached to an account |
| **Sign in with email code** | Access to an email address held on the account |

Google opens a window over the page. Apple, LinkedIn, GitHub, and Steam leave
the page and return to it once the provider has finished.

There is no registration form. An account is created by an administrator after
a request. See [Scopes and access](scopes.md).

### Email and password

1. Enter the email address and password.
2. Select **Sign in**, or press `Enter` in the password field.

### Emailed code

1. Select **Sign in with email code**.
2. Enter the email address.
3. Select **Send code**.
4. Enter the six digit code.
5. Select **Verify & Sign In**.

The code field accepts six characters. **Send code** becomes **Resend code**
once a code has been issued.

### Phone number

1. Select **Phone Number**.
2. Enter the number in full international format, for example `+447700900000`.
3. Select **Send Code**.
4. Enter the six digit code.
5. Select **Verify**.

Phone sign-in only signs in a number already attached to an account. It never
creates one. An unrecognised number returns to the sign-in card with a message
saying so. Attach the number from [Your account](account.md) first.

## After sign-in

The account is identified, then checked against the site that requested
sign-in. One of four screens follows.

| Screen | Meaning |
|--------|---------|
| **Signed in**, with a countdown | The account is approved and holds a scope for the requested site |
| **Pending Approval** | The account is not approved, or holds no scope for the requested site |
| **Access Denied** | The account is set to rejected |
| The sign-in card, with a message | The sign-in was refused. The message states why |

**Pending Approval** lists the address, name, and method the sign-in produced.
An empty address means the provider returned no verified email address, so the
sign-in matched no existing account.

The same **Pending Approval** screen appears for an account awaiting approval
and for an approved account missing a scope. The two are not distinguished on
screen.

## Returning to the originating site

A successful sign-in shows a five second countdown, then sends the browser to
the site that requested sign-in. **Manage account** on the same screen opens
the account page instead and cancels nothing; the countdown continues.

| Condition | Destination |
|-----------|-------------|
| Sign-in was requested by a site | That site |
| Sign-in page was opened directly | https://akn.me.uk |

The site being entered decides which scope is checked. Opening the sign-in page
directly checks the scope for the main site.

## Staying signed in

| Property | Detail |
|----------|--------|
| Session length | 14 days from sign-in |
| Coverage | One sign-in covers every akn site the account holds a scope for |
| Renewal | None. The session ends 14 days after it started |
| Per-site sessions | Individual sites hold their own session in addition, of their own length |

## Signing out

| Action | Effect |
|--------|--------|
| **Sign Out** on the account page | Returns to the sign-in page. The shared session is not ended |
| **Sign Out** in the administration area | Ends the shared session and returns to the sign-in page |
| **Sign Out** on **Pending Approval** or **Access Denied** | Returns to the sign-in card |
| Sign out on an individual site | Ends that site's own session only |

Signing out from the account page leaves the shared session in place, so other
akn sites remain reachable. Close the browser to end access from a shared
device.

## Related

- [Scopes and access](scopes.md) covers what decides whether a site can be reached.
- [Your account](account.md) covers attaching further sign-in methods.
- [Diagnostics](diagnostics.md) covers conditions encountered while signing in.
