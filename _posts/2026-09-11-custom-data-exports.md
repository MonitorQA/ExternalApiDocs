---
category: Custom data exports
categoryOrder: 16
url_path: '/custom-data-exports'
title: 'Custom data exports'
order: 1
layout: null
---

Start an asynchronous CSV export of a data set, poll until the export finishes, then download the file.

The API key user's role must include the `dataExports.accessCustom` permission. See [Role Permissions Reference](#/role-permissions-reference).

### Workflow

1. **Start the export** with the POST endpoint for the data set you need. The response is the export identifier.
2. **Poll status** with [Get custom data export](#/get-custom-data-export) (`GET /custom-data-exports/{taskId}`) until `status` is `2` (Succeeded) or `3` (Failed).
3. **Download files** from a succeeded export using [Get File](#/get-file-by-id) and each file `id` in the status response.

Completed exports are CSV files (`text/csv`). Column sets vary by data set and can include company metafields.

Use [Get accessible companies](#/get-companies) to obtain company IDs for the `companies` filter.

### Export types

| Path | Description | `dataType` |
|------|-------------|------------|
| `/custom-data-exports/pending-audits` | Pending audits | `0` |
| `/custom-data-exports/audit-items` | Audit items | `1` |
| `/custom-data-exports/sections` | Audit sections | `2` |
| `/custom-data-exports/corrective-actions` | Corrective actions | `3` |
| `/custom-data-exports/corrective-actions-activities` | Corrective action activities | `4` |
| `/custom-data-exports/completed-audits` | Completed audits | `5` |
| `/custom-data-exports/expired-audits` | Expired audits | `6` |
| `/custom-data-exports/all-audits` | All audits | `7` |

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
- `companies` is an array of company IDs. Only companies the API key user can access are used. If omitted or empty, no companies are included.
- `templateIds` and `auditObjectIds` apply only to pending audits, audit items, completed audits, expired audits, and all audits.

### Errors

Missing `dataExports.accessCustom` permission returns `409 Conflict` with message `permission-required/can-access-custom-data-exports`.

A missing export or an export that is not accessible with this API key returns `409 Conflict` with message `custom-data-export/no-access-or-not-found`.

Invalid date ranges return `400 Bad Request`.
