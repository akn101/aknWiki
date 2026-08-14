---
sidebar_position: 3
title: Scopes and access
---

# Scopes and access

A scope is a named grant that admits an account to one site or application.
An account holds a list of them. Where another akn product states that a
feature is restricted by akn ID scope, this is the model it refers to.

## What decides access

Two conditions must both hold before a site can be reached.

| Condition | Requirement |
|-----------|-------------|
| State | The account is approved |
| Scope | The account holds that site's scope, or the wildcard |

An approved account with no matching scope is stopped at the sign-in page, on
the same **Pending Approval** screen shown to an account awaiting approval.

## Grants

| Grant | Effect |
|-------|--------|
| A named scope, for example `thoughts` | Admits the account to that one site |
| `*` | Admits the account to every site |
| Administrator role | Opens the aknID administration area, and admits the account to sites that check the role directly |

The administration area labels scopes **Projects**. The two terms refer to the
same list.

The administrator role does not by itself satisfy the check made at sign-in.
An administrator holding no scope for the site being entered is held at
**Pending Approval**. Administrators are normally granted `*`.

## Scope names

The site being entered decides which scope is checked.

| Destination | Scope checked |
|-------------|---------------|
| https://startpage.akn.me.uk | `startpage` |
| https://thoughts.akn.me.uk | `thoughts` |
| https://cloud.akn.me.uk | `nextcloud` |
| https://akn.me.uk | `halcyon` |
| Any other destination | `halcyon` |

Applications signed in to through aknID rather than reached at an akn address
may require a scope of their own. Refusal there shows a page reading
`You don't have access to this app`, naming the account and the application.

## Requesting access

1. Select **Request access** on the sign-in page.
2. Enter the email address, name, and reason.
3. Select **Send verification code**.
4. Enter the six digit code sent to the address.
5. Select **Send Request**.

The reason field accepts up to 2000 characters and the name field up to 200.

Where the form reports an error after the code has been accepted, the request
has not been recorded. Contact the site operator directly in that case.

No reply is sent when a request is granted or refused. Sign in again to see
whether the state has changed.

## Granting access

The administration area is available at `/admin`, and at `/dashboard`. Access
requires the administrator role or the `*` scope. Accounts without either see
`Access denied`.

### The people list

| Tab | Contents |
|-----|----------|
| **All People** | Every person, with state, role, and granted scopes |
| **Pending** | People awaiting a decision |
| **Create Person** | A form for adding a person directly |

Counts of total, pending, and approved people appear above the tabs.

### Deciding a request

**Approve** and **Reject** appear on each row in the list. Selecting a row
opens the full record instead.

### Editing a person

| Field | Purpose |
|-------|---------|
| Name, Email | Identity shown throughout the administration area |
| Status | Pending, Approved, or Rejected |
| Role | User or Admin |
| Projects | The scopes the person holds |
| Groups, Tags | Labels for organising people |
| Secondary Emails, Phone Numbers | Further addresses and numbers belonging to the person |
| Linked Identities | The sign-in methods that resolve to this person |

Enter a scope, group, or tag by typing it and pressing `Enter` or `,`. Remove
one with its `x`, or press `Backspace` in an empty field to remove the last.

**Save Changes** applies the record. **Set Approved** and **Set Rejected**
apply the state together with any other edit made in the form.

### Linking sign-in methods to a person

Each sign-in method a person uses forms a separate identity. Linking joins them
so that all of them reach one account.

| Action | Use |
|--------|-----|
| **Link UID** | Attaches a known identity to this person |
| **Link via Email OTP** | Sends a code to an address and attaches it once the code is entered |
| **Unlink** | Detaches an identity from this person |

An identity left unlinked resolves to nobody and creates a second person on
next sign-in.

### Bulk actions

| Action | Effect |
|--------|--------|
| **Sync All Firebase Users** | Reconciles existing sign-in identities against the people list |
| **Sync CardDAV Contacts** | Reads the contact list and creates or updates people from it |

Both report counts of records scanned, created, and updated when they finish.

## Related

- [Signing in](signing-in.md) covers what a refused sign-in looks like.
- [Your account](account.md) shows the scopes an account holds.
- [Diagnostics](diagnostics.md) covers access conditions and resolutions.
