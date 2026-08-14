---
sidebar_position: 3
title: Moderation
---

# Moderation

The review queue is available at `/admin`. Access is restricted by akn ID
scope.

## Access requirements

An account qualifies by holding any one of the following:

| Grant | Value |
|-------|-------|
| Site scope | `thoughts` |
| Wildcard scope | `*` |
| Role | Administrator |

Accounts without a qualifying grant are returned to sign-in. Repeated
redirection indicates a valid account without a scope for this site rather than
a failed sign-in. Request the `thoughts` scope in that case.

Sessions last 30 days from sign-in.

See [akn ID](../../platform/akn-id/overview.md) for scope administration.

## Queue contents

The queue lists each submitted note with the date it arrived. Published notes
are listed separately below it.

## Actions

| Action | Applies to | Effect |
|--------|-----------|--------|
| Approve | A submitted note | Publishes it to the board |
| Reject | A submitted note | Deletes it |
| Add | New text entered directly | Publishes without review |
| Remove | A published note | Withdraws it from the board |

Approval and publication take effect immediately. There is no cache layer and
no delay before visitors see the change.

## Operating cautions

| Caution | Reason |
|---------|--------|
| Reload before removing a note | Removal acts on list position. A stale page can withdraw the wrong note |
| Avoid concurrent moderation | Two people acting at once can overwrite each other's decisions |
| Rejection is final | Rejected notes are deleted with no recovery path |
| Published notes lose their submission date | Only the note text is retained |

## Signing out

Sign-out is available from the queue header. It ends the session immediately
and returns to akn ID.

## Related

- [Overview](overview.md) covers the publication model.
- [Using the board](using.md) covers the submitter's view.
- [akn ID](../../platform/akn-id/overview.md) covers scope administration.
