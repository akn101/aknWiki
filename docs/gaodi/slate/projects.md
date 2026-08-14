---
sidebar_position: 2
title: Projects
---

# Projects

A project is the workspace for one product. Slate holds no multi product
project.

Every project holds at least one generation. A generation is one version of the
product, in the sense that a camera has a first model and a second model. A
generation passes through the six workflow stages.

## Creating a project

Select **New Project** in the sidebar.

1. Enter the **Name**.
2. Enter the remaining product details. Only **Name** and **Product Category**
   are required, and a category link fills the category for you.
3. Drop any starting files onto the upload area.
4. Confirm the type Slate assigns to each uploaded file.
5. Select **Create Project**.

Slate opens the new project. The account that created it becomes a project
admin.

### Project details

| Field | Purpose |
|-------|---------|
| **Name** | The Chinese product name. Required |
| **English Name** | The English product name |
| **Model Number** | The internal model code |
| **Product Category** | The category name. Required unless a category link is supplied |
| **Amazon category links** | One bestsellers or category address per line |
| **ASIN / product links** | One ASIN or product address per line |
| **Product Description** | A short description of the product |
| **Notes for AI** | Context, constraints and preferences. Added to every stage conversation in this project |
| Reference image | An image shown as the project icon. PNG, JPG or WEBP, under 5 MB |

Prefer a category link to a category name. A link carries both the marketplace
and the category node, which scopes research far more precisely. Paste one link
per marketplace.

ASINs and product links form the starting point of the competitor pool in the
Analyse stage.

### Starting files

Each file dropped onto the upload area is classified by type. Slate shows the
type it assigned and asks you to confirm or correct it. Suitable starting files
include product specifications, design files and existing user manuals.

## The project page

The project page opens on the active generation.

| Region | Contents |
|--------|----------|
| Header | Product name, status, category and model number |
| Stage progress | The six stages with their status. Each links to its stage page |
| Recent threads | The latest conversations across all stages of this generation |
| Recent files | The newest files in this generation |
| Generations | Every generation of this product. Each links to its Design stage |
| Members | The project member list with each member's project role |

## Project sub navigation

Expanding a project in the sidebar reveals four entries.

| Entry | Contents |
|-------|----------|
| **Market Reports** | Files of the market report type |
| **Specifications** | Files of the specification type |
| **Assets** | Brand assets and marketing images |
| **Settings** | Project details, members and generations |

## Editing a project

Open **Settings** under the project in the sidebar.

The form holds the same fields as the creation form. Select **Save changes** to
apply them. Only project admins can edit project details. Other members see the
form in read only form.

## Collaboration

The **Collaboration** panel on the project settings page controls who reaches
the project.

| Visibility | Who reaches the project |
|------------|------------------------|
| **Private** | Project members and scope administrators only |
| **Group** | Everyone in the owning group |
| **Company** | Anyone in the company, read only |

Two further settings sit beside it.

| Setting | Effect |
|---------|--------|
| **Owning group** | The department or team the project belongs to. A project belongs to at most one group |
| **Linked storefronts** | The Amazon storefronts this product sells on |

Left on **Auto**, visibility resolves to group visible when you belong to a
group, and to private otherwise. Only project admins can change these settings.

## Operations

The **Operations** area of a project covers work after launch. It holds the
Amazon report parser, recurring scheduled jobs, the reports those jobs produce,
and an anomaly panel.

| Feature | Availability |
|---------|--------------|
| Parse an Amazon Search Term or Business report | Available |
| Schedule a recurring market report, positioning analysis or compliance check | Available |
| Read the reports produced by scheduled jobs | Available |
| Demand forecasting | Not available |
| Advertising campaign management | Not available |
| Price, rating and stock anomaly alerts | Not available |

## Constraints

| Constraint | Detail |
|------------|--------|
| Products per project | One |
| Deleting a project | Not available |
| Starting a further generation | Not available from the interface |
| Project category | Required. A category link supplies it |
| Reference image size | 5 MB |

## Related

- [Overview](overview.md) covers roles and signing in.
- [Workflow stages](workflow-stages.md) covers what happens inside a stage.
- [Files](files.md) covers uploads, folders and file reading.
- [Jobs and review](jobs-and-review.md) covers scheduled jobs.
