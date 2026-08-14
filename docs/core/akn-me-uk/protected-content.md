---
sidebar_position: 4
title: Protected content
---

# Protected content

Parts of the site are withheld until access is granted. Access is granted by a
five digit code or by an akn ID sign-in.

## What is withheld

| Section | Effect without access |
|---------|----------------------|
| Work | Two entries are absent from the list and from the command palette |
| Flair | Withheld experiments are absent from the grid and from the command palette |
| Letters | Restricted letters are absent from the list. Unlisted and limited letters are listed with their text withheld |

Work and Flair show no placeholder and no count for a withheld entry. A visitor
without access has no indication that anything is missing.

## Entering an access code

1. Select the lock button in the header on About, Work, Flair, Photography, or
   Contact. On Letters, select the lock button beside the heading.
2. Enter the five digits. Focus advances with each digit.
3. Select **Next**.

`Backspace` clears the current box, then steps back to the previous one.
**Close** dismisses the dialog. Closing clears the digits.

| Outcome | What is shown |
|---------|---------------|
| Code accepted | A confirmation reading `Access Granted`. Withheld entries appear without a reload |
| Code rejected | The dialog closes with no message |

The dialog reports nothing on a rejected code. Entering the code through the
command palette instead returns `Invalid access code`.

## Signing in with akn ID

1. Open the access dialog by either lock button.
2. Select **Login with akn ID**.
3. Complete sign-in at akn ID.

Access follows the groups held by the account. Administrator accounts and
accounts holding a site wildcard receive everything.

An account without a grant for this site is refused with `Access not granted
for halcyon.`

Entering an access code while signed in attaches that code to the account
rather than to the browser.

## Duration

| Method | Duration | Renewal |
|--------|----------|---------|
| Access code | 24 hours from entry | Enter the code again |
| akn ID | 1 hour | Automatic while the akn ID session stands |
| Access code entered while signed in | Held against the account | None required |

## Access notice

The first section opened while access is held shows a notice reading
`Protected Content Unlocked`, with a request to respect confidentiality terms.
It appears once per browser session.

## Limitations

| Limitation | Detail |
|------------|--------|
| Removing access | Not available from the interface. Code access expires on its own |
| Reviewing what access is held | Not available. No list of granted items is shown |
| Requesting a code | Not available from the site. Contact the site operator |
| Feedback on a rejected code in the dialog | Not available |
| Sharing a protected entry | The link is of no use to a visitor without access |
| Recovering a forgotten code | Not available |

## Related

- [Using the site](using.md) covers the `/access` command in the command palette.
- [Letters](letters.md) covers restriction levels applied to written pieces.
- [Diagnostics](diagnostics.md) covers conditions encountered while requesting access.
