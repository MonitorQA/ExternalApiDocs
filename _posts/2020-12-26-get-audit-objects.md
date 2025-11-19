---
category: 5. Audit objects
url_path: '/audit/objects'
title: 'Get list of audit objects'
type: 'GET'
order: 5
layout: null
---

Retrieve a list of all audit objects belonging to your company. This endpoint provides a simple collection of audit objects with their basic identification information, ideal for populating selection lists.

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
    "id": "234567890-abcd-efgh-ijkl-mnopqrstuvwx",
    "name": "Warehouse Section B"
  },
  {
    "id": "345678901-bcde-fghi-jklm-nopqrstuvwxy",
    "name": "Quality Control Lab"
  }
]
```

For errors responses, see the [response status codes documentation](#/response-status-codes).
