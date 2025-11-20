---
category: 6. Audit object attributes
categoryOrder: 6
url_path: '/audit/objects/attributes/{id}'
title: 'Get Audit Object Attribute Details'
type: 'GET'
order: 2
layout: null
---

Retrieve detailed information about a specific audit object attribute, including all its available options and settings. This endpoint provides comprehensive attribute configuration data.

## Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| id | string | Yes | The unique identifier of the audit object attribute |

### Example Request

```http
GET /audit/objects/attributes/890123de-fghi-4567-890a-bcdef1234567
Host: api-external.monitorqa.com
X-API-KEY: abcdef12345
```

## Response

**Success Response**

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "options": [
    {
      "isDefault": true,
      "name": "High Priority",
      "id": "678901bc-defa-2345-6789-01bcdef12345"
    },
    {
      "isDefault": false,
      "name": "Medium Priority",
      "id": "789012cd-efab-3456-789a-12cdef123456"
    },
    {
      "isDefault": false,
      "name": "Low Priority",
      "id": "901234ef-ghij-5678-90ab-cdef12345678"
    }
  ],
  "name": "Priority Level",
  "id": "890123de-fghi-4567-890a-bcdef1234567"
}
```

For errors responses, see the [response status codes documentation](#/response-status-codes).
