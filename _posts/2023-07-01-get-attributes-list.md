---
category: 6. Audit object attributes
categoryOrder: 6
url_path: '/audit/objects/attributes/all'
title: 'Get Audit Object Attributes List'
type: 'GET'
order: 1
layout: null
---

Retrieve a complete list of all audit object attributes available in your organization. This endpoint provides comprehensive attribute data including all available options for each attribute.

### Example Request

```http
GET /audit/objects/attributes/all
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
    "options": [
      {
        "isDefault": true,
        "name": "Manufacturing",
        "id": "678901bc-defa-2345-6789-01bcdef12345"
      },
      {
        "isDefault": false,
        "name": "Warehouse",
        "id": "789012cd-efab-3456-789a-12cdef123456"
      }
    ],
    "name": "Department",
    "id": "890123de-fghi-4567-890a-bcdef1234567"
  },
  {
    "options": [
      {
        "isDefault": false,
        "name": "High",
        "id": "901234ef-ghij-5678-90ab-cdef12345678"
      },
      {
        "isDefault": true,
        "name": "Medium",
        "id": "012345fg-hijk-6789-01bc-def123456789"
      },
      {
        "isDefault": false,
        "name": "Low",
        "id": "123456gh-ijkl-789a-bcde-f12345678901"
      }
    ],
    "name": "Risk Level",
    "id": "234567hi-jklm-890a-bcde-f12345678902"
  }
]
```

For errors responses, see the [response status codes documentation](#/response-status-codes).
