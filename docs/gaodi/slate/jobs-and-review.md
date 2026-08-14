---
sidebar_position: 6
title: Jobs and review
---

# Jobs and review

Long running work runs as a job. Work that needs a person's approval waits in
the review inbox.

## The job queue

Open **Jobs** in the sidebar. The queue is shared: every member sees every job,
with the member who started it named against it.

| Column | Contents |
|--------|----------|
| **Type** | What the job does, for example **Extract pain points** or **Market report** |
| **Project** | The project the job belongs to |
| **Created** | When it was started |
| Status | **Pending**, **Running**, **Complete** or **Failed** |

| Control | Effect |
|---------|--------|
| **All** and **Mine** | Shows every job, or only your own |
| **Refresh** | Reloads the list |
| **Auto-refresh** | Reloads the list continuously |
| **Retry** | Restarts a failed job from its last checkpoint |
| **Cancel** | Stops a pending or running job |

### Outputs

A completed job lists what it produced.

| Output | Meaning |
|--------|---------|
| **File** | A file written to the project |
| **Report** | A report written to the project |
| **Thread reply** | A reply posted into the conversation that started the job |

A failed job carries **Error details** stating the reason.

### Cost

Each job shows its model cost, and the page shows a **Page total**.

| Reading | Meaning |
|---------|---------|
| An amount | The estimated cost of the model calls the job made |
| **No model calls** | The job used no model. The cost is genuinely zero |
| **Not priced** | The model has no configured price. The cost cannot be estimated and was not zero |
| **Not measured** | No cost data was reported |

Where some calls could not be priced, the figure shown is a floor and the note
says so.

### Duplicate work

Starting a stage action that another member already started reports **Already
started by another member** and starts nothing.

## Scheduled jobs

Recurring work is scheduled per project. Open **Operations** on the project, or
the **Scheduled jobs** tab of the **Jobs** page.

1. Select the **Job type**.
2. Select the **Cadence**: **Daily**, **Weekly** or **Monthly**.
3. Select **Create**.

| Job type | Produces |
|----------|----------|
| **A1 Market report** | A market report for the project |
| **B1 Positioning** | A positioning analysis |
| **C1 Compliance check** | A compliance checklist |

Each schedule shows its owner, its **Next run** and its **Last run**. Select
**Enable** or **Disable** to change whether it runs. A schedule that has not run
reads **Not run yet**.

Creating or switching a schedule requires the reviewer or admin role. Other
members see the list read only.

Reports produced by scheduled jobs appear under **Latest ops reports** on the
project's **Operations** page.

## The review inbox

The review inbox holds artifacts submitted for sign off. Open **Review Inbox**
in the sidebar. The sidebar entry carries the pending count.

Access requires the reviewer or admin role.

| Tab | Contents |
|-----|----------|
| **Pending** | Items awaiting a decision |
| **History** | Items already decided, with the person who decided them |

### Deciding an item

1. Select the item to open its detail view.
2. Read the **Artifact preview** and the **Job context**.
3. Enter a comment. The comment is optional.
4. Select **Approve** or **Reject**.

| Region | Contents |
|--------|----------|
| **Artifact preview** | The content submitted. Long content shows its opening |
| **Job context** | The **Input** and **Output** of the job that produced it |
| **Open file** | Opens the artifact in the file viewer |
| **View in source thread** | Opens the conversation the artifact came from |
| **All projects** | Filters the queue to one project |

An item another reviewer has already decided reads **This item is already
resolved**.

Rejecting an item does not strand its job. The job returns for another decision.

## Related

- [Workflow stages](workflow-stages.md) covers the actions that start jobs.
- [Projects](projects.md) covers the Operations area.
- [Administration](administration.md) covers roles and system settings.
- [Diagnostics](diagnostics.md) covers job and review conditions.
