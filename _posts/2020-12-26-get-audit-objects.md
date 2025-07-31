---
category: 5. Audit Objects
url_path: '/audit/objects'
title: 'Get list of audit objects'
type: 'GET'
order: 17
layout: null
---

Retrieve a list of all audit objects belonging to your company. This endpoint provides a simple collection of audit objects with their basic identification information, ideal for populating selection lists.

## Request Example

```http
GET https://api-external.monitorqa.com/audit/objects
X-API-KEY: abcdef12345
```

## Response

**Success Response**

```http
HTTP/1.1 200 OK
Content-Type: application/json

[
  {
    "id": "object-123",
    "name": "Manufacturing Line A"
  },
  {
    "id": "object-456",
    "name": "Warehouse Section B"
  },
  {
    "id": "object-789",
    "name": "Quality Control Lab"
  }
]
```

For errors responses, see the [response status codes documentation](#/response-status-codes).
