---
category: 12. Files
categoryOrder: 12
url_path: '/files/{id}'
title: 'Get File'
type: 'GET'
order: 1
layout: null
---

Retrieve a file by its unique identifier. Files can include images, documents, and other attachments uploaded during audits or corrective actions.

### Request Headers

| Header | Type | Required | Description |
|--------|------|----------|-------------|
| `X-API-KEY` | string | Yes | API authentication key |

### Path Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `id` | string | Yes | Unique identifier of the file |

### Query Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `withWatermark` | boolean | No | Whether to apply watermark to image files (default: `false`). Returns original file if watermarking is disabled in template settings |

### Example Request

```http
GET /files/123e4567-e89b-12d3-a456-426614174000?withWatermark=true
Host: api-external.monitorqa.com
X-API-KEY: abcdef12345
```

## Response

**Success Response**

```http
HTTP/1.1 200 OK
Content-Type: [varies by file type]

[File content - binary or text based on file type]
```


For errors responses, see the [response status codes documentation](#/response-status-codes).
