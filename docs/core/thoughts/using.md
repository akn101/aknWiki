---
sidebar_position: 2
title: Using the board
---

# Using the board

Reading and submitting are open to any visitor. Neither requires an account.

## Reading

The board loads on arrival at https://thoughts.akn.me.uk. No action is
required.

Notes render in columns sized to the viewport.

| Viewport | Columns |
|----------|---------|
| Phone | 1 |
| Small tablet or narrow window | 2 |
| Laptop and above | 3 |

| Property | Detail |
|----------|--------|
| Ordering | Fixed. Not user-controllable |
| Search | Not available |
| Filtering | Not available |
| Pagination | None. The full board loads at once |
| Empty state | Displays `nothing here yet` |

## Submitting a note

1. Select **leave a thought**.
2. Enter the note. The field accepts 160 characters and stops at the limit.
3. Select **send**.

The dialog confirms receipt and closes after two seconds.

### Discarding a draft

Any of the following closes the dialog without submitting:

| Action | |
|--------|--|
| Select **cancel** | |
| Press `Escape` | |
| Click outside the dialog | |

Drafts are not retained. Reopening the dialog presents an empty field.

## Constraints

| Constraint | Detail |
|------------|--------|
| Length | 160 characters. Enforced in the field and again on submission |
| Empty submissions | Rejected. Whitespace alone counts as empty |
| Revision | Unavailable once submitted |
| Withdrawal | Requires contacting the site operator |
| Rate limit | None applied |

## After submission

The note enters a review queue visible only to scope holders. Approval
publishes it to the board. Rejection deletes it.

Submission status is not exposed to the submitter. A note absent from the board
is either awaiting review or has been rejected, and the two cannot be
distinguished.

## Related

- [Overview](overview.md) covers the publication model and privacy properties.
- [Moderation](moderation.md) covers what happens to a note after submission.
- [Diagnostics](diagnostics.md) covers conditions encountered while submitting.
