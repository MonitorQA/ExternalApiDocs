---
category: Custom data exports
categoryOrder: 16
url_path: '/custom-data-exports/pending-audits'
title: 'Export pending audits'
type: 'POST'
order: 2
layout: null
---

Start an asynchronous CSV export of pending audits. The response is the export identifier. Poll [Get custom data export](#/get-custom-data-export) until the export finishes, then download files with [Get File](#/get-file-by-id). See [Custom data exports](#/custom-data-exports) for the full workflow.

The API key user's role must include the `dataExports.accessCustom` permission.

### Request Headers

| Header | Type | Required | Description |
|--------|------|----------|-------------|
| `X-API-KEY` | string | Yes | API authentication key |
| `Content-Type` | string | Yes | Must be `application/json` |

### Request Body Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `fromDate` | datetime | No | Start of the date range in UTC (`yyyy-MM-ddTHH:mm:ss.fffZ`). If omitted, defaults to two years before the current day |
| `toDate` | datetime | No | End of the date range in UTC (`yyyy-MM-ddTHH:mm:ss.fffZ`). Must be greater than or equal to `fromDate` when both are set. If omitted, defaults to the current day |
| `companies` | array[uuid] | No | Company IDs to include. Only companies the API key user can access are used. If omitted or empty, no companies are included. Use [Get accessible companies](#/get-companies) to list available IDs |
| `templateIds` | array[uuid] | No | Audit template IDs to include. Only templates the API key user can access are used |
| `auditObjectIds` | array[uuid] | No | Audit object IDs to include. Only audit objects the API key user can access are used |

### Example Request

```http
POST /custom-data-exports/pending-audits
Host: api-external.monitorqa.com
X-API-KEY: abcdef12345
Content-Type: application/json

{
  "fromDate": "2024-01-01T00:00:00.000Z",
  "toDate": "2024-12-31T23:59:59.999Z",
  "companies": ["123e4567-e89b-12d3-a456-426614174000"],
  "templateIds": ["456e7890-e89b-12d3-a456-426614174001"],
  "auditObjectIds": ["789e0123-e89b-12d3-a456-426614174002"]
}
```

## Response

**Success Response**

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "id": "a1b2c3d4-e5f6-789a-bcde-f01234567890"
}
```

### Response Fields

| Field | Type | Description |
|-------|------|-------------|
| `id` | uuid | Unique identifier of the export. Use it with [Get custom data export](#/get-custom-data-export) |

### Error Responses

**Permissions Error (409)**

```http
HTTP/1.1 409 Conflict
Content-Type: application/json

{
  "message": "permission-required/can-access-custom-data-exports"
}
```

Occurs when the API key user's role does not include `dataExports.accessCustom`.

For errors responses, see the [response status codes documentation](#/response-status-codes).
