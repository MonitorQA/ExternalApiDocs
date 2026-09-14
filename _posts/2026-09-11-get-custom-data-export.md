---
category: Custom data exports
categoryOrder: 16
url_path: '/custom-data-exports/{taskId}'
title: 'Get custom data export'
type: 'GET'
order: 10
layout: null
---

Retrieve the status of a custom data export started with any of the export POST endpoints. Poll this endpoint until `status` is `2` (Succeeded) or `3` (Failed). When the export succeeds, download each file with [Get File](#/get-file-by-id). See [Custom data exports](#/custom-data-exports) for the full workflow.

The `dataType` field in the response identifies which data set was exported.

### Request Headers

| Header | Type | Required | Description |
|--------|------|----------|-------------|
| `X-API-KEY` | string | Yes | API authentication key |

### Path Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `taskId` | uuid | Yes | Unique identifier of the export returned by an export POST endpoint |

### Example Request

```http
GET /custom-data-exports/a1b2c3d4-e5f6-789a-bcde-f01234567890
Host: api-external.monitorqa.com
X-API-KEY: abcdef12345
```

## Response

### Status values

| Value | Status | Description |
|-------|--------|-------------|
| `0` | Created | Export has been accepted and is waiting to start |
| `1` | In progress | Export is running |
| `2` | Succeeded | Export finished; download files from the `files` array |
| `3` | Failed | Export did not complete |

### Data types

| Value | Data type |
|-------|-----------|
| `PENDING_AUDITS` | Pending audits |
| `AUDIT_ITEMS` | Audit items |
| `SECTIONS` | Audit sections |
| `CORRECTIVE_ACTIONS` | Corrective actions |
| `CORRECTIVE_ACTIONS_ACTIVITIES` | Corrective action activities |
| `COMPLETED_AUDITS` | Completed audits |
| `EXPIRED_AUDITS` | Expired audits |
| `ALL_AUDITS` | All audits |

**Success Response**

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "id": "a1b2c3d4-e5f6-789a-bcde-f01234567890",
  "dataType": "PENDING_AUDITS",
  "status": 2,
  "files": [
    {
      "id": "b2c3d4e5-f6a7-890b-cdef-012345678901",
      "name": "pending-audits-export.csv",
      "contentType": "text/csv"
    }
  ],
  "createdAtUtc": "2026-09-11T10:00:00.000Z",
  "startedAtUtc": "2026-09-11T10:00:01.000Z",
  "completedAtUtc": "2026-09-11T10:00:15.000Z"
}
```

`files` is empty until the export succeeds. `startedAtUtc` and `completedAtUtc` are `null` until those times are set.

### Response Fields

| Field | Type | Description |
|-------|------|-------------|
| `id` | uuid | Unique identifier of the export |
| `dataType` | string | Data set of this export. See [Data types](#data-types) |
| `status` | number | Current export status. See [Status values](#status-values) |
| `files` | array | Files produced by a succeeded export. Empty until `status` is `2` |
| `files[].id` | uuid | File identifier for [Get File](#/get-file-by-id) |
| `files[].name` | string | File name |
| `files[].contentType` | string | MIME type of the file. Succeeded exports use `text/csv` |
| `createdAtUtc` | datetime | When the export was created (UTC) |
| `startedAtUtc` | datetime | When processing started (UTC). `null` until the export starts |
| `completedAtUtc` | datetime | When processing finished (UTC). `null` until the export finishes |

### Error Responses

**Export Not Found (409)**

```http
HTTP/1.1 409 Conflict
Content-Type: application/json

{
  "message": "custom-data-export/no-access-or-not-found"
}
```

Occurs when the export does not exist or is not accessible with this API key.

For errors responses, see the [response status codes documentation](#/response-status-codes).
