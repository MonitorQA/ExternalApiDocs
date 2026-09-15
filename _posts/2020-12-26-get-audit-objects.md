---
category: Audit objects
categoryOrder: 5
url_path: '/audit/objects'
title: 'Get list of audit objects'
type: 'GET'
order: 5
layout: null
---

Retrieve a list of all audit objects belonging to your company. This endpoint provides a simple collection of audit objects with their basic identification information, ideal for populating selection lists.

### Request Headers

| Header | Type | Required | Description |
|--------|------|----------|-------------|
| `X-API-KEY` | string | Yes | API authentication key |

### Example Request

```http
GET /audit/objects
Host: api-external.monitorqa.com
X-API-KEY: abcdef12345
```

## Response

**Success Response**

```http
HTTP/1.1 200 OK
Content-Type: application/json

[
  {
    "id": "789abcde-f123-4567-8901-234567890123",
    "name": "Manufacturing Line A"
  },
  {
    "id": "23456789-abcd-4ef0-a012-234567890123",
    "name": "Warehouse Section B"
  },
  {
    "id": "34567890-bcde-4f01-a012-345678901234",
    "name": "Quality Control Lab"
  }
]
```

For error responses, see the [response status codes documentation](#/response-status-codes).
