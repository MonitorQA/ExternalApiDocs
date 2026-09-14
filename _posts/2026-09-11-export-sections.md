---
category: Custom data exports
categoryOrder: 16
url_path: '/custom-data-exports/sections'
title: 'Export sections'
type: 'POST'
order: 4
layout: null
---

Start an asynchronous CSV export of audit sections. The response is the export identifier. Poll [Get custom data export](#/get-custom-data-export) until the export finishes, then download files with [Get File](#/get-file-by-id). See [Custom data exports](#/custom-data-exports) for the full workflow.

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
| `companies` | array[uuid] | No | Company IDs to include. Only companies the API key user can access are used. If omitted or empty, the export includes no companies. Pass accessible IDs from [Get accessible companies](#/get-companies) |

### Example Request

```http
POST /custom-data-exports/sections
Host: api-external.monitorqa.com
X-API-KEY: abcdef12345
Content-Type: application/json

{
  "fromDate": "2024-01-01T00:00:00.000Z",
  "toDate": "2024-12-31T23:59:59.999Z",
  "companies": ["123e4567-e89b-12d3-a456-426614174000"]
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

For error responses, see the [response status codes documentation](#/response-status-codes).
