---
sidebar_position: 3
title: Documentation standards
---

# Documentation standards

The rules every page in this wiki follows. This page is for authors. Readers
wanting to navigate the wiki efficiently should read the aknWiki section
instead.

## Audience

Pages are written for the person who uses a product. Not the person who
deploys it, and not the person who maintains it.

The following never appear on a page:

| Excluded | Reason |
|----------|--------|
| Environment variables and configuration keys | Not actionable by a user |
| Deployment and build commands | Not actionable by a user |
| Repository paths, function names, library names | Not actionable by a user |
| Database tables and storage schemas | Not actionable by a user |
| Hosting and infrastructure detail | Not actionable by a user |

URL paths a person types into a browser are permitted.

Source code is read to establish what is true. It is not the subject of the
page.

## Register

Declarative. Specific. Short sentences.

Each product opens with a capability statement: what the product allows users
to do, followed by what controls exist over it.

Correct:

```text
aknThoughts allows users to post short notes publicly on a bulletin board.
Access and review controls are available and can be set by the organisation
using akn ID scopes.
```

Incorrect. Narrative sequencing walks the reader through an experience instead
of stating a capability:

```text
Thoughts is a single page holding short notes from anyone who visits. You read
what other people have left. You can add your own.
```

## Prohibited constructions

| Construction | Example | Correction |
|--------------|---------|------------|
| Em dash and en dash | Any use as punctuation | Comma, colon, semicolon, full stop, or parentheses |
| Dramatic appositive | "The API was Bedrock, and it predates the session." | Split into two sentences or delete the second clause |
| Useless trailing clause | "Notes occupy one of three states. The board displays the third only." | "Notes occupy one of three states." |
| Rhetorical reversal | "It isn't a tool; it's a platform." | State what it is |
| Marketing adjectives | powerful, seamless, robust, intuitive, simply, easily | Delete |
| Filler openers | "It's worth noting", "At its core", "Under the hood" | Delete |
| Vague quantifiers | "a bunch of", "tons of" | Give the number |

The useless trailing clause is the most common fault. Before publishing, reread
the last sentence of every paragraph and delete it if it adds nothing.

## Required forms

| Rule | Application |
|------|-------------|
| Tense and voice | Present tense, active voice |
| Instructions | Imperative. "Select", not "You can select" |
| Ordered actions | Numbered list, one action per step |
| Enumerable content | Table, not prose |
| Interface labels | Bold, exactly as displayed |
| Keys and typed paths | Backticks |
| Spelling | British |

## Page structure

Each product is a folder of pages rather than one page. Previous and next
navigation generates from page order.

| File | Position | Contents |
|------|----------|----------|
| `overview.md` | First | Metadata table, capability statement, capabilities table |
| `using.md` | Second | The primary task |
| Task pages | Middle | One page per distinct job |
| `diagnostics.md` | Last | Conditions, causes, resolutions |

Four to seven pages suits most products. Split where there is content to
separate. Thin products take fewer pages.

### Metadata table

Every overview opens with an unlabelled four-row table.

| Field | Contents |
|-------|----------|
| URL | Where the product is reached |
| Description | One line stating what the product allows users to do |
| Access | Who can use it, and which parts are restricted |
| Pricing | What it costs |

Field names are fixed. Do not substitute "Cost" for "Pricing" or "What this is"
for "Overview".

### Capabilities table

Lists what the product does and what it does not do. Rows marked
`Not available` are required where a user might reasonably expect a capability
that does not exist.

### Diagnostics table

Columns are `Condition`, `Cause`, `Resolution`. Group by user task, one table
per group.

Causes are stated in terms of the user's situation.

| Correct cause | Incorrect cause |
|---------------|-----------------|
| Note retrieval failed. Failures are silent. | The storage read threw and the catch block is empty. |

## Evidence

Every statement is supported by the source read to produce the page. Behaviour
is not inferred from a package name.

Where behaviour cannot be established, it is omitted. Pages state what a
product does. They do not carry caveats about the documentation process.

Limitations are documented honestly. Where a user cannot undo an action, the
page says so. Where a failure is silent, the page says so.

## Naming

Products use the `aknX` convention where one applies. A product carrying its
own name uses that name. Brands are not invented for products that lack one.

## Links

Pages link to siblings within their own product folder. Cross-product links are
added centrally after a section is complete. The site rejects broken links at
build time.
