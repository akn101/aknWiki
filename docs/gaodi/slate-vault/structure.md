---
sidebar_position: 2
title: Structure
---

# Structure

The vault has two top level folders. All examples on this page use invented
names.

```text
brands/
projects/
```

## Brand entries

One folder holds one brand kit.

```text
brands/example-brand/
  guidelines.md
  palette.yml
  refs/
```

| Item | Holds |
|------|-------|
| `guidelines.md` | Voice and tone, and the do and do not rules for copy |
| `palette.yml` | Colours by role: primary, secondary, accent, neutral, background |
| `refs/` | Reference images: logo, product shots, lifestyle photography, packaging |

Brand entries sit outside the project folders. The brand applied to a project
is set in Slate. Slate reads the guidelines, the palette, and the reference
images when it writes listing copy and marketing images.

## Project entries

One folder holds one project.

```text
projects/example-camera-12/
  project.md
  gen-1/
    design/
    analyse/
    voc/
    iterate/
    generate/
  uploads/
```

| Item | Holds |
|------|-------|
| `project.md` | The project record: names, product code, category, and the notes Slate is given |
| `gen-1/` | The first generation of work on the product |
| `uploads/` | Files supplied by the operator |

## Generations

A generation is one pass of work on a product. Generations are numbered from
one. A second pass writes to `gen-2` and leaves `gen-1` untouched.

## Stage folders

Each generation holds one folder per stage. A stage folder appears only after
that stage produces a document.

| Folder | Holds |
|--------|-------|
| `design` | Product specifications |
| `analyse` | Competitor datasets, gap analyses, profit models, marketplace listing collections |
| `voc` | Customer review reports and product problem analyses |
| `iterate` | Revised specifications drawn from customer feedback |
| `generate` | Listing copy and marketing images |

## Uploads

Uploaded files are kept in `uploads` exactly as supplied. Slate does not
rewrite them.

Each PDF, spreadsheet, and Word document is read once at upload. The text is
written beside the original as a companion Markdown file, so the content can be
read and searched. Companion files are hidden from the file list inside Slate.

An upload stays in `uploads` even after it is tagged to a generation and a
stage. The tag is held in Slate rather than in the folder name.

## Related

- [Overview](overview.md) covers access and version history.
- [Conventions](conventions.md) covers naming and metadata.
