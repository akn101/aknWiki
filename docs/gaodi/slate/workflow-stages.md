---
sidebar_position: 3
title: Workflow stages
---

# Workflow stages

A generation passes through six stages in order. Stages may be revisited and
repeated at any time. Reaching a stage does not require the previous stage to be
complete.

Open a stage from the stage progress list on the project page, or from the
numbered circles at the top of any stage page.

## The six stages

| Number | Stage | What the stage does | Primary action |
|--------|-------|--------------------|----------------|
| 1 | **Design** | Produces and revises a product specification from consumer intent and competing products | **Start Analysis** |
| 2 | **Analyse** | Finds competitors, compares price and specification, and reports the gap against the current specification | **Compile Competitors** |
| 3 | **VOC** | Clusters customer pain points from reviews and returns into a report and a factory dataset | **Extract Pain Points** |
| 4 | **Iterate** | Combines analysis, VOC findings and notes into an improved specification version | **Draft New Spec Version** |
| 5 | **Generate** | Produces listing copy and images that follow the brand guidelines | **Generate** |
| 6 | **Reflect** | Not available. The stage opens and shows **Coming soon** in place of its action | None |

The Analyse stage carries eight research modules of its own. See
[The Analyse stage](analysis.md).

## The stage page

| Region | Contents |
|--------|----------|
| Stage header | The six numbered stages. The current stage is highlighted |
| Welcome text | What this stage does, and the note **You can come back anytime!** |
| File rail | An upload area and a file finder filtered to this stage's file types |
| Conversation | The messages of the current thread |
| Action bar | The primary action, and any secondary actions for this stage |
| Thread switcher | Every thread in this stage, plus **New thread** |

## Holding a conversation

1. Enter the message. Press `Enter` to send, or `Shift+Enter` for a new line.
2. The reply streams into the thread as it is produced.
3. Select **Stop** to interrupt a reply.

An interrupted reply is marked in the thread and its content is carried into the
next turn.

| Feature | Detail |
|---------|--------|
| Project context | The project record, the current specification, recent files and **Notes for AI** are supplied to the model on every turn |
| Model | Selected from **Model**. Leave on **Default (stage routing)** to use the stage's own model |
| Activity | Each tool the model uses appears as a chip: **Searching**, **Reading page**, **Saving file**, **Generating image** and others |
| Sources | Cited pages are listed under **Sources** below the reply |
| Retry | **Retry** resends the last message after a failure |

### Attachments

1. Select **Attach**, or drop files onto the conversation.
2. The files are listed above the composer.
3. Send the message.

Attach up to ten files per turn. Each file is limited to 25 MB. Slate reads PDF,
Excel, Word, CSV, Markdown and plain text files, and reads images directly.

### Skills

Skills are written playbooks the model can load: keyword research, FBA fee
calculation, competitor analysis and others.

1. Type `/` in the composer.
2. Move through the list with the arrow keys.
3. Press `Enter` to add the skill to this turn.

Invoke up to ten skills per turn. Slate also loads the skills relevant to the
current stage without being asked. Press `Escape` to close the picker.

### Threads

A stage holds any number of threads. Use a second thread to run a separate line
of investigation.

| Action | Effect |
|--------|--------|
| **New thread** | Starts an empty thread in this stage |
| **Rename thread** | Renames the thread. Type a name and press `Enter` |
| **Archive thread** | Hides the thread from the recent lists |
| **Restore** | Returns an archived thread to the active list |

## Running a stage action

Select the primary action in the bottom right of the conversation. Slate starts
a job, shows its progress inline, and writes the output to the project files.

| Condition | Behaviour |
|-----------|-----------|
| Job running | Progress appears inline with a link reading **View in Jobs** |
| Job complete | The file lists refresh automatically |
| Job failed | The failure is shown with the reason. Retrying resumes from the last checkpoint |
| Another member already started it | The button reports **Already started by another member** and starts nothing |

Running a stage action requires the operator project role or above.

### Secondary actions

Some stages carry extra actions beside the primary one.

| Stage | Secondary action | Requires |
|-------|-----------------|----------|
| Design | **Positioning** | A VOC conclusion in this generation |
| Analyse | **Market report** | Nothing |
| VOC | **Synthesis brief** | The product problem report in this generation |
| Generate | **Generate manual** | A product specification in this generation |
| Generate | **Compliance check** | Nothing |

A secondary action whose requirement is unmet is disabled. Hover the button to
read what is missing. Material from an earlier generation is never reused.

## The VOC stage

The VOC stage turns review exports and returns exports into a product problem
report and a dataset the factory can act on.

1. Upload the review export and the returns export through the file rail.
2. Select **Extract Pain Points**.

Slate finds the uploaded files itself. It produces a deterministic report with
severity bands, an evidence count for each problem, and a trace from each piece
of evidence back to its file, sheet, row and ASIN. A separate summary written by
the model is produced alongside it.

| Property | Detail |
|----------|--------|
| Personal data | Reviewer names and profile addresses are hashed at ingestion. Profile images are discarded |
| Evidence | Up to three customer quotes per problem, and up to eight problems per product line. Any withheld count is stated under the table |
| Returns reasons | Grouped into a top six table per product line. Ambiguous reason codes are listed separately for you to place |
| Carrier and warehouse damage | Counted as its own category, never as a product fault |

### Category return rate comparison

The returns export carries no sales figure, and category baselines are external
market knowledge. Both rates must therefore be entered by hand.

1. Open the return rate panel in the VOC stage.
2. Select **Add row**.
3. Enter the product family, the site, the category rate and your own rate.
4. Select **Save**.

Slate derives the percentage point gap, the multiple and the pressure verdict on
save. The figures you enter travel into a report the factory reads, and are
marked **UNVERIFIED** throughout. Left empty, the comparison section does not
appear in the report at all.

## The Generate stage

The Generate stage produces listing copy and product images from the latest
specification. Select **Generate v1** to produce the first draft.

| Feature | Detail |
|---------|--------|
| Fields | Title, **About this item** bullets, **Product description** and **Backend search terms** |
| Counters | Each field shows characters or bytes used against its cap |
| Compliance | Each field carries a badge listing its errors and warnings. Select the badge to read them |
| Preview | **Desktop** and **Mobile**. Mobile marks where the title is cut |
| Tracked changes | A word level comparison against the previous version |
| Lock | A locked field is skipped when the draft is regenerated |
| **Tell AI** | Sends a fix instruction for one field into the conversation |
| **Send for review** | Sends one field to a chosen reviewer |
| Images | Seven roles: **Main**, **Lifestyle**, **Infographic**, **Dimensions**, **Material**, **Comparison**, **Secondary** |
| Image export | **Download all images (ZIP)** |
| Versions | **Save as new version**. Earlier versions remain readable |

The price shown beside the copy comes from the Analyse stage price bands and
carries the **UNVERIFIED** fee marking.

## The Iterate stage

The Iterate stage combines the analysis, the VOC findings and your notes into a
new specification version.

| Panel | Contents |
|-------|----------|
| **Output Sets** | Every specification version produced in this generation |
| **Final Files** | The files marked as final for this generation |

## Related

- [The Analyse stage](analysis.md) covers the eight research modules.
- [Files](files.md) covers uploads and reading the files a stage produces.
- [Jobs and review](jobs-and-review.md) covers job progress and approvals.
- [Diagnostics](diagnostics.md) covers conditions encountered in a stage.
