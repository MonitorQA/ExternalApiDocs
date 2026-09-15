---
category: Custom data exports
categoryOrder: 16
url_path: '/custom-data-exports'
title: 'Custom data exports'
order: 1
layout: null
---

Start an asynchronous CSV export of a data set, poll until the export finishes, then download the file.

### Workflow

1. **Start the export** with the POST endpoint for the data set you need. The response is the export identifier.
2. **Poll status** with [Get custom data export](#/get-custom-data-export) (`GET /custom-data-exports/{taskId}`) until `status` is `2` (Succeeded) or `3` (Failed).
3. **Download files** from a succeeded export using [Get File](#/get-file-by-id) and each file `id` in the status response.

Completed exports are CSV files (`text/csv`). Column sets vary by data set and can include company metafields.

Use [Get accessible companies](#/get-companies) to obtain company IDs for the `companies` filter.

### Permissions

The API key user must have [`dataExports.accessCustom`](#/role-permissions-reference) in every company included in the export. Company membership from [Get accessible companies](#/get-companies) is not enough.

### Export types

| Path | Description | `dataType` |
|------|-------------|------------|
| `/custom-data-exports/pending-audits` | Pending audits | `PENDING_AUDITS` |
| `/custom-data-exports/audit-items` | Audit items | `AUDIT_ITEMS` |
| `/custom-data-exports/sections` | Audit sections | `SECTIONS` |
| `/custom-data-exports/corrective-actions` | Corrective actions | `CORRECTIVE_ACTIONS` |
| `/custom-data-exports/corrective-actions-activities` | Corrective action activities | `CORRECTIVE_ACTIONS_ACTIVITIES` |
| `/custom-data-exports/completed-audits` | Completed audits | `COMPLETED_AUDITS` |
| `/custom-data-exports/expired-audits` | Expired audits | `EXPIRED_AUDITS` |
| `/custom-data-exports/all-audits` | All audits | `ALL_AUDITS` |

Poll any export with [Get custom data export](#/get-custom-data-export) (`GET /custom-data-exports/{taskId}`). The `dataType` field in the status response identifies which data set was exported.

### Status values

| Value | Status | Description |
|-------|--------|-------------|
| `0` | Created | Export has been accepted and is waiting to start |
| `1` | In progress | Export is running |
| `2` | Succeeded | Export finished; download files from the `files` array |
| `3` | Failed | Export did not complete |

### Filters

All POST body fields are optional.

- `fromDate` and `toDate` use UTC format `yyyy-MM-ddTHH:mm:ss.fffZ`. If both are set, `toDate` must be greater than or equal to `fromDate`. If omitted, the range is the last two years through the current day.
- `companies` is an array of company IDs. Only companies the API key user can access and where that user has custom data export permission ([`dataExports.accessCustom`](#/role-permissions-reference)) are used. Companies without access or without that permission are ignored. If omitted or empty, the export uses the current company (the same permission is required there). Pass accessible IDs from [Get accessible companies](#/get-companies).
- `templateIds` and `auditObjectIds` apply only to pending audits, audit items, completed audits, expired audits, and all audits.

### Errors

A missing export or an export that is not accessible with this API key returns `409 Conflict` with message `custom-data-export/no-access-or-not-found`.

Invalid date ranges return `400 Bad Request`.
