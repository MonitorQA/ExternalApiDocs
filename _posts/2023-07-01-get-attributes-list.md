---
category: 10. Audit Object Attributes
url_path: '/audit/objects/attributes/all'
title: 'Get Audit Object Attributes List'
type: 'GET'
order: 1
layout: null
---

Retrieve a complete list of all audit object attributes available in your organization. This endpoint provides comprehensive attribute data including all available options for each attribute.

## Request Example

```http
GET https://api-external.monitorqa.com/audit/objects/attributes/all
X-API-KEY: abcdef12345
```

## Response

**Success Response**

```http
HTTP/1.1 200 OK
Content-Type: application/json

[
  {
    "options": [
      {
        "isDefault": true,
        "name": "Manufacturing",
        "id": "option-mfg-001"
      },
      {
        "isDefault": false,
        "name": "Warehouse",
        "id": "option-wh-001"
      }
    ],
    "name": "Department",
    "id": "attr-dept-001"
  },
  {
    "options": [
      {
        "isDefault": false,
        "name": "High",
        "id": "option-high-001"
      },
      {
        "isDefault": true,
        "name": "Medium",
        "id": "option-med-001"
      },
      {
        "isDefault": false,
        "name": "Low",
        "id": "option-low-001"
      }
    ],
    "name": "Risk Level",
    "id": "attr-risk-001"
  }
]
```

For errors responses, see the [response status codes documentation](#/response-status-codes).
