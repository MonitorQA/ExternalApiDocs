---
category: 2. Audits
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
| `auditId` | string | Yes | Unique identifier of the completed audit |

### Query Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `reportType` | integer | No | Report format type: `0` = Regular, `1` = Summary, `2` = Full (default: `0`) |
| `includePhotos` | boolean | No | Whether to include photos in the report (default: `false`) |

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

**Report Types:**
- **Regular (0):** Standard audit report with basic information
- **Summary (1):** Condensed report highlighting key findings
- **Full (2):** Comprehensive report with all details and context

For errors responses, see the [response status codes documentation](#/response-status-codes).
