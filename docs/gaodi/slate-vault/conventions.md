---
sidebar_position: 3
title: Conventions
---

# Conventions

Naming and metadata rules for the vault. All examples on this page use invented
names.

## Folder names

| Folder | Pattern | Example |
|--------|---------|---------|
| Project | English product name in lower case, words joined by hyphens, then the project number | `example-camera-12` |
| Project, where the name is in Chinese only | `project-` then the project number | `project-12` |
| Generation | `gen-` then the generation number | `gen-1` |
| Brand | Brand name in lower case, words joined by hyphens | `example-brand` |

The project number is part of the folder name. Two products with the same name
therefore keep separate folders.

## File names

| File | Pattern | Example |
|------|---------|---------|
| Document written by Slate | Title in lower case, words joined by hyphens, then `-v` and the version number | `example-camera-specification-v3.md` |
| Project record | Fixed name, no version number | `project.md` |
| Uploaded original | The name it was supplied under, with `-v1` added | `example-returns-v1.xlsx` |
| Text of an uploaded document | The upload name, then `.extracted.md` | `example-returns-v1.xlsx.extracted.md` |
| Version kept after a clash | The document name, then `.conflict-` and a short code | `spec-v3.conflict-a1b2c3d.md` |

Version numbers count up from one. Each new version is a new file. Slate never
overwrites a numbered document.

Chinese file names are supported throughout.

## Metadata

Every Markdown document Slate writes opens with a metadata block. Data files
and images carry no block.

```text
---
project: example-camera-12
generation: 1
stage: voc
type: voc_report
version: 2
date: '2026-07-24'
source_job: 481
source_thread: null
---
```

| Field | Value |
|-------|-------|
| `project` | The project folder name |
| `generation` | The generation number. Empty for uploads |
| `stage` | The stage name. Empty for uploads |
| `type` | The document type. See the table below |
| `version` | The version number, matching the file name |
| `date` | The date the document was written |
| `source_job` | The Slate run that produced the document. Empty for uploads and for chat edits |
| `source_thread` | The chat that produced the document. Empty otherwise |

Two further fields appear when they apply.

| Field | Value |
|-------|-------|
| `change_note` | Why a revision was made. Added when a document is edited through chat |
| `sources` | The numbered citations the document used, matching the source list in the body |

## Document types

| Type | Meaning |
|------|---------|
| `specification` | Product specification |
| `market_report` | Competitor and market analysis |
| `voc_report` | Customer review analysis |
| `dataset` | Tabular data, such as a competitor or returns export |
| `copy` | Listing copy |
| `marketing_image` | Generated product or lifestyle image |
| `manual` | Product manual or instruction booklet |
| `brand_asset` | Brand kit material |
| `positioning` | Product line positioning |
| `profit_model` | Cost and margin model |
| `factory_brief` | Instructions for the factory |
| `misc` | Anything not covered above, including extracted text |
| `ops_report` | Reserved. No stage writes this type |

## The project record

`project.md` holds the settings for one project. Slate rewrites it whenever
those settings change.

| Field | Value |
|-------|-------|
| `slug` | The project folder name |
| `name` | The product name as entered |
| `name_en` | The English product name. Empty when none is set |
| `sku` | The product code. Empty when none is set |
| `category` | The product category |

The body of the record holds two optional sections.

| Section | Purpose |
|---------|---------|
| `## Description` | What the product is and which markets it serves |
| `## Notes for AI` | Standing instructions Slate applies to every document in the project |

## Adding an entry

### A new project

1. Create the project in Slate.
2. Enter the name, the English name, the product code, and the category.

The project folder and the project record are written automatically. Do not
create a project folder by hand.

### A new document

1. Run the stage in Slate, or request the change in chat.
2. Wait for the run to finish.

The document is written into the stage folder with the next version number.

### A new upload

1. Select the upload control in Slate.
2. Choose the file.
3. Confirm or correct the document type Slate suggests.

Slate suggests a type from the file name, the file extension, and the text
inside the file. A confirmed type is never changed again.

### A new brand kit

1. Create a folder under `brands`.
2. Add `guidelines.md` with the voice, tone, and copy rules.
3. Add `palette.yml` with the colours by role.
4. Add a `refs` folder and place the reference images in it.

Brand kits are added by hand. No stage writes to `brands`.

## Editing in Obsidian

| Edit | Supported |
|------|-----------|
| Change the text of a document | Yes |
| Add your own metadata fields, such as a tag or a reviewer | Yes |
| Rename, edit, or remove a file in `uploads` | Yes |
| Add or edit a brand kit | Yes |
| Rename or renumber a document written by Slate | No. The document drops out of Slate and its citations break |
| Rename any of the standard metadata fields | No. The document drops out of filtered lists |
| Edit a document while Slate is writing a new version of it | No. Both versions are kept and must be merged by hand |
| Remove a companion text file | Permitted. It is written again on the next read |

Text belongs to the operator. File names, standard metadata fields, and version
numbers belong to Slate.

Slate re-reads the vault every five minutes.

## Related

- [Overview](overview.md) covers access and version history.
- [Structure](structure.md) covers the folders and what lives in each.
