---
sidebar_position: 3
title: Documentation conventions
---

# Documentation conventions

Every product is documented to the same pattern. The pattern is described here
once so that each product page can be read quickly.

## Page types within a product

| Page | Answers |
|------|---------|
| Overview | What the product is, who may use it, what it can and cannot do |
| Task page | How to carry out one job |
| Diagnostics | What to do when something does not work |

Start at the overview. It carries the metadata table and the capability table,
which together establish whether the product does what is needed and whether
the reader may use it.

Substantial products carry several task pages. A product with one task page has
one job.

## Capability tables

A capability table appears on every product overview. It lists what the product
does, and who can do it.

| Column | Contents |
|--------|----------|
| Capability | An action a user can take |
| Availability | Who may take it, or `Not available` |

Availability takes one of these forms.

| Value | Meaning |
|-------|---------|
| Any visitor | No account is required |
| A named group of account holders | Sign-in is required, and the account must qualify |
| Not available | The product does not do this |

## Not available rows

A row marked `Not available` states that the product does not offer the
capability. It describes the product as it stands and carries no implication
about future work.

Absence is not a statement either way. Where a capability appears in no row,
the page does not cover it.

## Diagnostics tables

A diagnostics page lists conditions users encounter. Conditions are grouped by
task, one table per group, so the table to read is the one matching what was
being attempted.

| Column | Contents |
|--------|----------|
| Condition | What is observed, such as a message on screen or an action having no effect |
| Cause | The situation that produces the condition |
| Resolution | The action that clears it |

A resolution reading that no action is available means no user action will
change the condition.

Diagnostics pages close with escalation instructions naming what to report and
where to report it.

## akn ID scope notes

Some products restrict features to accounts holding a named akn ID scope. Where
a page states this, it names the scope and the area it covers.

| Note on the page | Meaning |
|------------------|---------|
| Restricted by akn ID scope | Sign-in is required, and the account must hold the named scope |
| A scope named after the product | Grants the restricted features of that product only |
| Wildcard scope `*` | Grants restricted features across products |
| Administrator role | Qualifies in place of a named scope |

An account without the required scope is refused the restricted area. Returning
repeatedly to sign-in indicates a valid account missing the scope rather than a
failed sign-in.

Scope notes name the scope to request. They do not grant it.

## Text conventions

| Convention | Meaning |
|------------|---------|
| Bold text | A label reproduced exactly as it appears in the product |
| Backticked text | A key to press, a path to type, or an exact value |
| A numbered list | Steps carried out in order, one action per step |
| A URL path such as `/admin` | Appended to the product URL and entered in the address bar |

Product names appear as plain text. A page links only to other pages within the
same product.

## Related

- [Overview](overview.md) covers what the wiki does and does not do.
- [Finding pages](using.md) covers the sidebar and page navigation.
