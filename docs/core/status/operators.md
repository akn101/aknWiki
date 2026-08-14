---
sidebar_position: 4
title: Operator tasks
---

# Operator tasks

The operator panel is at `/admin`. It manages active incidents and the list of
monitored services.

## Access

Visitors without a valid session are sent to akn ID and returned to the panel
after signing in. Repeated redirection indicates an account that is not
permitted to operate this page.

Select **← status** to return to the public page.

## Panel contents

| Section | Contents |
|---------|----------|
| active incidents | Every open incident, each with a **resolve** control |
| create incident | A form for declaring a new incident |
| monitored urls | Every monitored service, each with a **remove** control |
| add url | A form for adding a service to monitoring |

With no open incidents, the first section displays `no active incidents`.

## Declaring an incident

1. Open `/admin`.
2. Enter the incident title in **title**. Required.
3. Enter the affected service in **service**. Required.
4. Enter the affected address in **url**. Optional.
5. Enter the detail in **description**. Optional.
6. Select **create incident**.

The message `Incident created` appears for three seconds and the active list
reloads. Visitors see the incident the next time they load the status page.

Write the title in the form visitors already see: the service name followed by
the severity, such as `Letters Extended Outage`.

Enter the service name exactly as it appears on the status page. The name is
displayed as typed.

## Updating an incident

| Change | Availability |
|--------|--------------|
| Correct the title, description, or address | Not available |
| Change the status badge between investigating and monitoring | Not available |
| Set or change an expected resolution time | Not available |
| Resolve the incident | Available |

An incident cannot be edited once created.

## Resolving an incident

1. Locate the incident under **active incidents**.
2. Select **resolve** on its row.

The message `Resolved` appears and the entry leaves the active list. No
confirmation is requested and the action cannot be reversed from the panel.

## Adding a monitored service

1. Enter the name to display in **name**. Required.
2. Enter the address to check in **url**. Required.
3. Select **add url**.

The message `Added` with the name appears and the list reloads. The service is
checked from the next scheduled run. Its card shows a grey history bar and
`--%` until results accumulate.

## Removing a monitored service

1. Locate the service under **monitored urls**.
2. Select **remove** on its row.
3. Confirm the prompt `Remove` followed by the service name.

The card stops appearing on the status page from the next page load. Recorded
history for that service is retained but no longer displayed.

## Operating cautions

| Caution | Detail |
|---------|--------|
| Resolution is immediate | There is no confirmation prompt and no undo |
| Incidents cannot be edited | Check the title and description before creating |
| A declared incident may not persist | Incident records are rebuilt from recorded check history. An entry with no matching recorded failures may be replaced |
| Names are free text | A service name that does not match the status page leaves visitors unable to connect the incident to a service |
| Removal keeps history | Past incidents for a removed service remain listed and show `Unknown URL` |
| Renaming is not available | Removing and adding under a new name starts a new history and empties the bar |
| Actions run one at a time | Controls are disabled while an action is in progress. Wait for the confirmation rather than selecting again |
| Confirmations are brief | Messages clear after three seconds. Errors appear in red beside the heading |
| No sign-out control | Close the tab to leave the panel |

## Related

- [Incidents](incidents.md) covers how declared and automatic incidents are displayed.
- [Reading the page](using.md) covers the monitored services list.
- [Diagnostics](diagnostics.md) covers conditions encountered in the panel.
