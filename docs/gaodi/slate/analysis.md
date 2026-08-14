---
sidebar_position: 4
title: The Analyse stage
---

# The Analyse stage

The Analyse stage decides whether a product is worth entering the market with.
It carries eight research modules and produces the opportunity score, the profit
model and the entry recommendation. Later stages read its conclusions.

Move between modules with the tabs across the top of the stage.

| Tab | Module | Answers |
|-----|--------|---------|
| **01 Overview** | Overview | How good the opportunity is, and how much of the assessment is backed by data |
| **02 Competitors** | Competitor pool | Who the product competes with, and whether the pool is deep enough |
| **03 Market size** | Market size | How large the category is, how concentrated, and which way it is moving |
| **04 Keywords** | Keywords | Which search terms carry the demand |
| **05 VOC** | Customer voice | What customers complain about. Produced in the VOC stage |
| **06 Profit model** | Profit model | What the unit earns at each price and cost |
| **07 Risk** | Risk register | What has not been checked yet |
| **08 Conclusion** | Entry recommendation | Go, Conditional Go or No-Go, and what holds it down |

## How Slate reports a missing figure

These rules apply across every module.

| Display | Meaning |
|---------|---------|
| A hatched bar with **Not measured** | No data for this figure. It is not a value of zero |
| `0` | A measured zero |
| **Provisional** in amber | The number is correct, and under half the framework carries data |
| **UNVERIFIED** | A fee or tariff constant dated 2024 that has not been re-verified |
| **Operator input** | A value you entered, used exactly as typed |
| **Not modelled** | A charge left out of the calculation. It does not mean the charge is zero |

A missing sub indicator is never scored zero. It is dropped from the
calculation, and the remaining weights are rescaled.

## 01 Overview

The overview carries the opportunity score out of 100, its four dimensions, the
framework coverage and the evidence confidence.

| Dimension | Weight | Reads high when |
|-----------|--------|-----------------|
| **Market demand** | 30% | Sales scale, search demand, trend and breadth are strong |
| **Competitive opportunity** | 25% | The market is easy to enter. Stronger competition scores lower, not higher |
| **Product fit** | 20% | The specification already meets what the market asks for |
| **Profit potential** | 25% | Margin, break-even ACOS, downside case and price buffer hold up |

**Evidence confidence** is reported separately and is not part of the score. It
states how much of what the conclusion rests on is backed by reliable data or
human verification. It does not state how likely the answer is to be correct.

**Next best actions** lists what is currently unmet. Each entry carries a **Go**
link to the module that fills it.

## 02 Competitors

Select **Generate** to collate similar products from the web and the
marketplaces. No upload is required.

Slate reports how many rows are real product pages. Search pages, category
landing pages and unpriced pages are tagged **not a product page** and are
excluded from the coverage counts. To add a competitor precisely, paste its link
into the stage conversation.

### Tiers

Assign each competitor a tier. Slate suggests a tier from price alone and marks
the suggestion for you to confirm. Price cannot separate a direct competitor
from a substitute.

| Tier | Target depth |
|------|--------------|
| **Direct** | 10 to 15 |
| **Benchmark** | 5 |
| **Substitute** | 3 to 5 |

The coverage bar states the gap in full, for example direct 6 against a target
of 10 to 15, four short.

### Output

| Action | Produces |
|--------|----------|
| **Titles + links (Markdown)** | A list of the selected rows |
| **Titles + links (text)** | The same list as plain text |
| **Excel dataset (.xlsx)** | A spreadsheet of the selected rows |
| **Enhanced dataset** | A spreadsheet with extracted specifications. Runs as a background job |
| **Generate Report** | A gap report written to the project files |

## 03 Market size

A project that has not been researched shows what a run would produce and offers
**Run market research**. Select it, then select **Refresh** once the job
finishes. The page never claims the work is finished before it is.

| Section | Contents |
|---------|----------|
| Browse node decision | The category node the research settled on, and the candidate nodes considered |
| Market size, concentration and trend | The measured figures, each with a source and a reliability tag |
| Sample validation | The checks behind the confidence grade |
| Key findings | The conclusions drawn from the above |

The node decision is worded two ways, and they are not equally strong. Several
high selling competitors clustering in one node means the node is the real
category. Competitors dispersed across nodes means Slate took the densest node,
which is a weaker call and worth checking by hand.

| Reliability | Treat as |
|-------------|----------|
| **High** | Usable as it stands. Still worth confirming against the sample checks |
| **Medium** | An estimate. Confirm the definition and the order of magnitude |
| **Low** | Indicative only. Verify by hand before any conclusion rests on it |

The full report and its raw data tables are written to the project files. The
page carries only the key findings and a link reading **Open the full report**.
Figures are never compared across marketplaces.

A run that finishes without obtaining a single figure says so and names the
likely cause. Blank is shown in place of invented numbers.

## 04 Keywords

Filled by the same market research run as **03 Market size**. It lists the
primary search terms with their monthly searches, and the demand and trend
figures that rest on them.

These terms decide which competitors count and which category is the real one,
and they are where the advertising and copy work starts.

## 05 VOC

Review themes and return risk are produced in the VOC stage. Open the VOC stage
to upload the review and returns exports, or to read the product problem report
already produced there.

## 06 Profit model

Every figure here is calculated deterministically. No model is involved.

### Price bands

Price bands appear automatically once similar products are collated. Each band
carries a review weighted density and its representative listings. Select **Use
this band** to apply it.

### Cost scenarios

1. Enter the minimum and maximum unit cost.
2. Adjust the price and the conversion rate.

Slate reports the unit cost, margin, break-even ACOS and viable CPC under a
**Downside**, **Base** and **Upside** case. Where cost exceeds price the cards
read **Not viable** instead of printing a negative bid.

### Fee inputs

Leave the fee fields blank to use the 2024 constants, which are marked
**UNVERIFIED**. A value you enter is used exactly as typed and is labelled
**Operator input** in the scenarios and in the report.

| Field | Covers |
|-------|--------|
| **FBA fee (per unit)** | Fulfilment cost per unit |
| **Referral rate (0-1)** | Marketplace referral commission |
| **Returns provision rate (0-1)** | Provision set aside for returns |
| **Coupon (per unit)** | Coupon cost per unit |

The per unit breakdown names the source of every line. A charge left out reads
**Not modelled**.

### Price point report

Select **Price-point report** to write the current price and cost scenarios to
the project files as a cited profit model report.

## 07 Risk

Eight standing risks are listed, each stating what to check.

| Status | Meaning |
|--------|---------|
| **Pending** | Not yet looked at |
| **Confirmed open** | The risk is real and unresolved |
| **Mitigated** | Addressed |
| **Accepted** | Real, and accepted as it stands |

Record the evidence or the decision in the note field. An unconfirmed risk never
blocks the conclusion. It caps the conclusion at **Conditional Go** and is named
there.

## 08 Conclusion

The conclusion is bound by the opportunity score, the evidence confidence, the
framework coverage and the risk sign off together. It recalculates as evidence
arrives.

| Verdict | Meaning |
|---------|---------|
| **Go** | No unmet conditions |
| **Conditional Go** | Proceed, subject to the conditions listed |
| **No-Go** | Do not proceed |

**Unmet conditions** names every reason the verdict is not a clean **Go**.
Select **Recalculate** after changing evidence, and **Export decision memo** to
write the conclusion to the project files.

## Related

- [Workflow stages](workflow-stages.md) covers the other five stages.
- [Files](files.md) covers reading the reports this stage produces.
- [Jobs and review](jobs-and-review.md) covers job progress and approvals.
- [Diagnostics](diagnostics.md) covers conditions encountered during research.
