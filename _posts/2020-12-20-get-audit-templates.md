---
category: 4. Audit Templates
url_path: '/audit/templates'
title: 'Get audit templates list'
type: 'GET'
order: 4
layout: null
---

Retrieve a simple list of all audit templates with their ID and name pairs. This endpoint provides a lightweight response ideal for populating dropdown menus and template selection interfaces.

### Example Request

```http
GET /audit/templates
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
    "id": "567890ab-cdef-1234-5678-90abcdef1234",
    "name": "Safety Inspection Template"
  },
  {
    "id": "678901bc-defa-2345-6789-01bcdef12345",
    "name": "Equipment Maintenance Check"
  },
  {
    "id": "789012cd-efab-3456-789a-12cdef123456",
    "name": "Compliance Audit Form"
  }
]
```

For errors responses, see the [response status codes documentation](#/response-status-codes).
