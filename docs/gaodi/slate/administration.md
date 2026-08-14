---
sidebar_position: 7
title: Administration
---

# Administration

Administration covers accounts, the organisation directory, brand kits, report
templates, the skills library and spend. Open **Settings** in the sidebar.

Which tabs appear depends on the role of the account.

| Tab | Visible to |
|-----|-----------|
| **Connections** | Admins |
| **Model Routing** | Admins |
| **Brand Kits** | Admins |
| **Report Templates** | Admins and reviewers |
| **Users & Roles** | Admins |
| **Organization** | Admins and scope administrators |
| **Feedback** | Admins and reviewers |
| **Vault** | Admins |
| **Alerts & Language** | Admins |
| **Usage & Spend** | Admins |
| **Profile** | Everyone |

## Users and roles

Registration is closed. Accounts are created here.

1. Open **Users & Roles**.
2. Select **Add User**.
3. Enter the **Email**, the **Display name** and the **Role**.
4. Select **Create user**.

Slate shows a temporary password once and never again. Hand it to the person
over a secure channel such as a WeCom direct message or in person. Never send it
by email or in a group chat.

| Action | Effect |
|--------|--------|
| Change **Role** | Moves the account between operator, reviewer and admin |
| **Deactivate** | Blocks the account from signing in |
| **Reactivate** | Restores a deactivated account |

You cannot deactivate or demote your own account.

### ERP token

Each account may carry its own **Lingxing token**. Once bound, that account's
ERP queries use the stores that token reaches. The token is stored encrypted and
is never shown again after saving.

| Action | Effect |
|--------|--------|
| **Bind** | Attaches a token to the account |
| **Replace** | Replaces the stored token |
| **Clear** | Removes the token |

## Organisation

The **Organization** tab holds groups, storefronts and role grants. Scope
administrators see only the groups and storefronts they administer.

### Groups

A group is a department or team. A project belongs to at most one group.

| Field | Purpose |
|-------|---------|
| **Name** and **English name** | The group name |
| **Description** | What the group covers |

Each group carries a roster. Add members, mark one as **Lead**, and remove
members who have left. A group no longer in use can be deactivated rather than
removed.

### Storefronts

A storefront is an Amazon marketplace the company sells on. Storefronts are
synchronised from the ERP or created by hand.

| Action | Effect |
|--------|--------|
| **Sync now** | Pulls the storefront list from the ERP and reports what was added, updated and deactivated |
| **New storefront** | Creates one by hand, with a name and a marketplace code |

### Role assignments

Role assignments grant group administrator or storefront administrator powers.
Choose the scope type, the scope, the role and the person, then select
**Grant**. Every assignment records who granted it and can be revoked.

## Connections and model routing

**Connections** lists every external data source, sign-in method and storage
target with its configuration state and the time it last succeeded.

**Model Routing** lists which model each stage and task uses, and the fallback
chain behind it.

Both tabs are read only. Connector keys cannot be entered in the browser. An
administrator configures them outside Slate.

## Brand kits

A brand kit defines the voice and the colours creative generation follows.

1. Open **Brand Kits**.
2. Select **New kit**.
3. Enter the **Name**.
4. Add palette entries. Name each colour by its role, with a hex value.
5. Add tone descriptors as free text.
6. Select **Create**.

Creating a kit also creates its folder in the document store, holding the
guideline documents and reference images. Guideline documents are edited in the
document store, not in Slate.

A kit still linked to a project cannot be deleted. Reassign those projects, or
disable the kit instead.

## Report templates

Each report producer carries a skeleton template. Sections marked as slots are
filled from data. Everything else passes through exactly as written.

| Action | Effect |
|--------|--------|
| **Insert** | Adds a slot at the cursor |
| **Save as new version** | Saves the edit as a new version, with an optional note |
| **Roll back to this** | Makes an earlier version active |
| **Restore default** | Returns to the built in template. Custom versions stay in the history |

Deleting a slot removes its section from the report. Reordering slots reorders
the report.

## Skills library

Skills are written playbooks the model loads during a conversation. Open
**Skills** in the sidebar. Access requires the reviewer or admin role.

| Kind | Editable |
|------|----------|
| **Shipped** | No. Shipped playbooks arrive with the release and are read only |
| **Custom** | Yes |

### Adding a skill

1. Select **New skill**.
2. Enter the **Skill name (slug)**. Lowercase letters, digits and hyphens only. It cannot match a shipped playbook.
3. Enter the **Category**, the **Chinese title** and the one line English **Description**.
4. Set **Depth** to **Ordinary** or **Deep research**, and the **Minimum sources**.
5. List the **Required tools**. An unknown tool name is rejected.
6. Write the body in Markdown.
7. Select **Create skill**.

A skill's **Scope** decides who can load it: company wide, one group or one
storefront.

### Bulk import

Select **Bulk import** and drop Markdown files or ZIP bundles.

| Constraint | Detail |
|------------|--------|
| Formats | `.md` files and `.zip` bundles |
| Files per import | 50 |
| File size | 500 KB |
| Re-uploading a name | Overwrites it as a new version |
| Scripts and assets inside a bundle | Not imported |

The result lists what was created, updated and rejected.

## Usage and spend

Open **Usage** in the sidebar. Access requires the admin role.

| Panel | Contents |
|-------|----------|
| Summary | Total cost, calls, input tokens and output tokens |
| **Daily spend trend** | Cost rolled up by day |
| **By model**, **By task type**, **By project** | Cost broken down three ways |
| **Endpoint latency** | Recent median and 90th percentile response time per operation |

Cost is an estimate in US dollars. A latency figure marked **Est.** rests on too
few samples and uses a preset estimate.

## Feedback triage

The **Feedback** tab lists every report submitted through the feedback button.
Filter by status, reply to the reporter in the thread, and move the report
through its statuses.

| Status | Meaning |
|--------|---------|
| **New** | Not yet looked at |
| **Triaged** | Read and categorised |
| **In progress** | Being worked on |
| **Fixed** | Resolved |
| **Won't fix** | Closed without a change |
| **Answered** | A question, answered |

## Alerts and language

**Alerts & Language** holds the failover and digest alert thresholds and the
interface language. The language setting also sits in the sidebar footer.

## Related

- [Overview](overview.md) covers roles and signing in.
- [Projects](projects.md) covers project level collaboration settings.
- [Jobs and review](jobs-and-review.md) covers the review inbox.
- [Diagnostics](diagnostics.md) covers administration conditions.
