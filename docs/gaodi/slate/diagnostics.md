---
sidebar_position: 8
title: Diagnostics
---

# Diagnostics

Observed conditions and their resolutions.

## Signing in

| Condition | Cause | Resolution |
|-----------|-------|------------|
| **Sign-in failed. Check your email and password.** | The email address or the password is wrong | Re-enter both. Ask an administrator if the account was recently created |
| The sign-in screen appears after previous use | The session passed seven days | Sign in again |
| The **Phone code** tab is absent | Code sign-in is not enabled for the organisation | Sign in with a password or with WeCom |
| **No account is linked to this phone number.** | The number is not bound to an account | Sign in with a password, then bind the number under **Settings** then **Profile** |
| **That code is invalid or has expired.** | The code was mistyped, or more than five minutes passed | Select **Resend code** |
| **Too many attempts. Please try again in a moment.** | Codes were requested repeatedly | Wait, then request one code |
| **SMS is temporarily unavailable.** | Code delivery is not working | Sign in with a password |
| **That phone number is already bound to another account.** | Another account holds the number | Use a different number, or ask an administrator to unbind it |
| **WeCom login is unavailable right now.** | WeCom sign-in cannot be reached | Sign in with a password |

## Projects

| Condition | Cause | Resolution |
|-----------|-------|------------|
| **Project name is required** | The **Name** field is empty | Enter the product name |
| **Product category is required** | No category name and no category link | Enter a category, or paste an Amazon category link |
| The category stays empty after pasting a link | The link carries no category Slate recognises | Enter the category by hand |
| **Some files failed to upload** | One or more starting files did not upload | The project was still created. Upload the files again from a stage file rail |
| The project details form cannot be edited | The account is not a project admin | Ask a project admin to make the change |
| The **Collaboration** panel is read only | The account is not a project admin | Ask a project admin to change visibility |
| The **Generations** list holds only one entry | Starting a further generation is not available in the interface | Continue in the existing generation |

## Stage conversations

| Condition | Cause | Resolution |
|-----------|-------|------------|
| **Generation failed** | The model call did not complete | Select **Retry** |
| The reply stops partway and is marked as interrupted | **Stop** was selected, or the connection dropped | The partial reply carries into the next turn. Send the next message |
| **You can attach up to 10 files** | The attachment limit was reached | Send the message, then attach the rest on the next turn |
| **Attachment upload failed** | The upload did not complete | Attach the file again. Check it is under 25 MB |
| **Attach a project to upload files by drag-and-drop** | Quick Chat has no project attached | Select **Select project** |
| **You can invoke up to 10 skills** | The skill limit was reached | Remove a skill, or split the request across turns |
| **No matching skills** | No skill name matches what was typed | Clear the text after `/` and read the full list |
| **This stage is not available yet** | The stage is Reflect, which is not available | Use the other five stages |
| **This project has no generation yet** | The project holds no generation | Ask an administrator |

## Running stage actions

| Condition | Cause | Resolution |
|-----------|-------|------------|
| **Already started by another member** | The same action is already running | Watch it in **Jobs**. Do not start a second run |
| A secondary action is disabled | Its precondition is unmet for this generation | Hover the button to read what is missing, then produce it in this generation. Material from an earlier generation is never reused |
| The job fails and lists an error | The pipeline stopped part way | Select **Retry**. It resumes from the last checkpoint |
| The action button is absent | The account does not hold the operator project role | Ask a project admin for the operator role |

## Research and analysis

| Condition | Cause | Resolution |
|-----------|-------|------------|
| A figure shows a hatched bar and **Not measured** | No data was obtained for that figure | Run the module that supplies it. Blank is not a value of zero |
| **This run obtained no data** | The market research completed and the data source returned nothing, usually because it has no credential | Ask an administrator to configure the source, then run it again |
| The score is marked **Provisional** | Under half the assessment framework carries data | Fill the missing dimensions. The number is correct but is not yet a conclusion |
| **Not yet assessable** | No dimension carries data | Enter a price and a cost range in **06 Profit model** |
| A cost scenario reads **Not viable** | Cost exceeds price | Lower the cost or raise the price |
| A competitor row shows **no price** | The page did not state a price Slate could read | Slate withholds rather than guessing. Enter the price by hand if needed |
| A row is tagged **not a product page** | The link is a search or category page, or has no price | Paste the individual product link into the stage conversation |
| Tier coverage reads short of target | Fewer competitors are tiered than the target band | Collate more products, or assign tiers to untiered rows |
| The conclusion is capped at **Conditional Go** | One or more risks are unconfirmed, or a condition is unmet | Read **Unmet conditions** on **08 Conclusion** and settle each one |
| A fee is marked **UNVERIFIED** | The figure is a 2024 constant not re-verified for the current year | Enter your own value in the fee inputs |
| The return rate comparison is missing from the VOC report | No return rate rows were entered | Enter the rows in the VOC stage and run the report again |

## Files

| Condition | Cause | Resolution |
|-----------|-------|------------|
| **Preview not available for this file type** | Slate cannot render this format | Select **Download** and open it locally |
| **You do not have access to this file** | The account is not a member of the project | Ask a project admin to add the account |
| The session is reported as expired | The session passed seven days | Sign in again |
| A spreadsheet shows fewer rows than the file holds | Reading is capped at 200 rows and 40 columns per sheet | Download the file to read it in full |
| The model does not use an uploaded file | The file is over 25 MB, or is in a format Slate cannot read | Supply the content as PDF, Excel, Word, CSV, Markdown or plain text |
| **Only .xlsx or .csv report files are supported** | The report parser was given another format | Export the report again as `.xlsx` or `.csv` |
| **Unrecognised report type** | The file is not an Amazon Search Term or Business report | Check the export before uploading it again |
| The result is marked **Truncated** | The row cap was reached | Split the report and parse each part |
| **You have read-only access to this project, so you cannot comment.** | The account holds the viewer project role | Ask a project admin for a higher role |

## Jobs and review

| Condition | Cause | Resolution |
|-----------|-------|------------|
| **Could not load jobs** | The job list could not be retrieved | Select **Retry** |
| **Scheduling is not available on this server yet** | Scheduling is not enabled in this environment | Ask an administrator |
| **This job type is not registered** | The chosen recurring job is not enabled | Choose another job type |
| A cost reads **Not priced** | The model used has no configured price | Treat the page total as a floor. The work was not free |
| A cost reads **No model calls** | The job used no model | No action. The cost is genuinely zero |
| **This item is already resolved** | Another reviewer decided it first | Reload the inbox |
| **Review Inbox** is absent from the sidebar | The account holds the operator role | Ask an administrator for the reviewer role |
| A schedule cannot be created or switched | The account is not a reviewer or admin | Ask a reviewer or an administrator |

## Administration

| Condition | Cause | Resolution |
|-----------|-------|------------|
| **That email is already registered** | An account already holds that address | Reactivate the existing account instead of creating a new one |
| **You cannot deactivate or demote your own account** | The action targets the signed in account | Ask another administrator to make the change |
| A temporary password was lost | The password is shown once and is not stored in readable form | Ask an administrator. It cannot be retrieved |
| **Projects still link this kit** | A brand kit in use cannot be deleted | Reassign those projects, or disable the kit |
| A skill import is rejected | The file is over 500 KB, is not `.md` or `.zip`, is missing its name or category, or names a tool that does not exist | Correct the file and import it again |
| **Settings** shows a single tab | The account reaches only that tab | No action. The other tabs need a higher role |
| A connector reads **Not configured** | No key is set for that source | An administrator configures it outside Slate. Keys are never entered in the browser |

## Reporting a problem

Select **Feedback** in the bottom right corner of any page.

1. Choose the **Type**: **Bug**, **Suggestion** or **Question**.
2. Choose the **Urgency**.
3. Describe what you were doing, what happened, and what you expected.
4. Attach a screenshot. Screenshots can be attached from a project page.
5. Select **Submit**.

Slate records the page, the project, the conversation and the build with the
report. Replies appear under **My feedback**. Recent changes to Slate are listed
under **What's new**.

## Related

- [Overview](overview.md)
- [Projects](projects.md)
- [Workflow stages](workflow-stages.md)
- [The Analyse stage](analysis.md)
- [Files](files.md)
- [Jobs and review](jobs-and-review.md)
- [Administration](administration.md)
