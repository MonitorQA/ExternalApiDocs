---
category: 4. Audit Templates
url_path: '/audit/templates'
title: 'Get audit templates list'
type: 'GET'
order: 15
layout: null
---

Retrieve a simple list of all audit templates with their ID and name pairs. This endpoint provides a lightweight response ideal for populating dropdown menus and template selection interfaces.

## Request Example

```http
GET https://api-external.monitorqa.com/audit/templates
X-API-KEY: abcdef12345
```

## Response

**Success Response**

```http
HTTP/1.1 200 OK
Content-Type: application/json

[
  {
    "id": "template-123",
    "name": "Safety Inspection Template"
  },
  {
    "id": "template-456",
    "name": "Equipment Maintenance Check"
  },
  {
    "id": "template-789",
    "name": "Compliance Audit Form"
  }
]
```

For errors responses, see the [response status codes documentation](#/response-status-codes).
