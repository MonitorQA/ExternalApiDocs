---
category: Audits
categoryOrder: 2
url_path: '/audit/complete/{auditId}/report-pdf'
title: 'Get audit pdf report'
type: 'GET'
order: 2
layout: null
---

Download a PDF report of a completed audit. The report contains all audit items, responses, and optional photos in a formatted document.

### Request Headers

| Header | Type | Required | Description |
|--------|------|----------|-------------|
| `X-API-KEY` | string | Yes | API authentication key |

### Path Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `auditId` | uuid | Yes | Unique identifier of the completed audit |

### Query Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `reportType` | integer | No | When set, controls layout: `0` = Regular (details, no summary), `1` = Summary (summary, no details), `2` = Full (both). When omitted, use `includeSummary` / `includeDetails` below |
| `includeSummary` | boolean | No | Include summary section (used when `reportType` is not set) |
| `includeDetails` | boolean | No | Include details section (used when `reportType` is not set) |
| `includePhotos` | boolean | No | Include photos in the PDF (default: `false`) |
| `includeNAAnswers` | boolean | No | Include not-applicable answers (default: `true` on server) |

### Example Request

```http
GET /audit/complete/123e4567-e89b-12d3-a456-426614174000/report-pdf?reportType=2&includePhotos=true
Host: api-external.monitorqa.com
X-API-KEY: abcdef12345
```

## Response

**Success Response**

```http
HTTP/1.1 200 OK
Content-Type: application/pdf

[Binary PDF file content]
```

**reportType values (when provided):**
- **Regular (0):** Details section, no summary
- **Summary (1):** Summary section, no details
- **Full (2):** Summary and details

For errors responses, see the [response status codes documentation](#/response-status-codes).
