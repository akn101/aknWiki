---
sidebar_position: 5
title: Files
---

# Files

Every file a stage produces and every file you upload is held in the project's
document store. Slate reads that store, and the store is also readable outside
Slate. See Slate Vault for the store itself.

## File types

Each file carries one type. The type drives which stage finder shows it and
which folder it appears in.

| Type | Holds |
|------|-------|
| **Specification** | A product specification |
| **Market Report** | Market research and gap reports |
| **VOC Report** | Pain point reports and review summaries |
| **Dataset** | Spreadsheets and normalised report data |
| **Copy** | Listing copy versions |
| **Marketing Image** | Generated product images |
| **Manual** | User manuals |
| **Brand Asset** | Brand guideline documents and reference images |
| **Positioning** | Positioning analyses |
| **Profit Model** | Price point and profit reports |
| **Factory Brief** | Findings written for the factory |
| **Ops Report** | Reports produced by scheduled jobs |
| **Misc** | Anything else |

## Uploading

Files are uploaded from the file rail of any stage page, from the project
creation form, or by dropping them onto a conversation.

1. Drag the files onto the upload area, or select it to choose files.
2. Slate detects each file's type and shows it.
3. Confirm or correct the type.

| Constraint | Detail |
|------------|--------|
| Maximum file size | 25 MB |
| Readable formats | PDF, Excel, Word, CSV, Markdown, plain text and images |
| PDF reading | The first 50 pages |
| Spreadsheet reading | The first 200 rows and 40 columns of each sheet |
| Text reading | The first 200,000 characters |

A file larger than the cap, or in a format Slate cannot read, is still stored.
Only its contents are unavailable to the model. Truncation is stated on the
file.

## Finding a file

### From a stage

The file rail on every stage page carries a finder pre filtered to that stage's
file types. Set **TYPE** to widen it, or search by name. Selecting a file
attaches it as input to the stage.

### From the sidebar

Expanding a project reveals **Market Reports**, **Specifications** and
**Assets**. Each opens a folder view.

| Control | Effect |
|---------|--------|
| Type filter | Restricts the list to one file type |
| Generation filter | Restricts the list to one generation |
| **Search files** | Matches the file name |
| **List** and **Grid** | Switches the layout |

## Reading a file

Open a file to read its contents beside its details.

| Detail | Meaning |
|--------|---------|
| **Type** | The file type |
| **Version** | The version number of this file |
| **Stage** | The stage that produced it |
| **Generation** | The generation it belongs to |
| **Git commit** | The recorded change it arrived in |
| **Created** and **Updated** | Timestamps |
| **Path** | Its location in the document store |
| **Document properties** | Any metadata fields written into the file |

Markdown files render as formatted text. Spreadsheets and CSV files render as a
table, with **Raw** and **Table** switching the view. Long tables show the first
rows and say how many are shown. A file type Slate cannot render reads
**Preview not available for this file type**.

Select **Download** to save the original file.

## Comments

Comments hold review notes left by the model and replies left by your team.

1. Open the file.
2. Enter the comment.
3. Select **Post**.

A comment may be anchored to a point in the document. Model authored notes are
bylined with the model that wrote them. Members with the viewer project role can
read comments and cannot post them.

## Versions

Slate writes a new version rather than overwriting a file. Earlier versions
remain readable. The version number appears against the file in every list.

## Parsing an Amazon report

The report parser turns an Amazon Search Term or Business report into a
structured dataset, with every row traceable back to its source row.

1. Open **Operations** on the project.
2. Select **Choose report**.
3. Select **Parse**.

| Constraint | Detail |
|------------|--------|
| Formats | `.xlsx` and `.csv` |
| Maximum size | 25 MB |
| Row cap | Reached files are marked **Truncated** |
| Permission | Operator project role or above |

The result names the report type it recognised, the rows kept, the rows skipped
and the dataset written. An unrecognised report reads **Unrecognised report
type**. Select **Open dataset** to read the output.

## Confidentiality

Uploaded review and returns exports carry customer data as supplied. Reports
Slate produces from them are written from anonymised data: reviewer names and
profile addresses are hashed at ingestion and profile images are discarded.
Uploaded originals keep whatever they contained.

## Related

- [Workflow stages](workflow-stages.md) covers the stage file rail.
- [The Analyse stage](analysis.md) covers the reports that stage writes.
- [Projects](projects.md) covers the project folders.
- [Diagnostics](diagnostics.md) covers file conditions and resolutions.
