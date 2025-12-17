---
category: Audit Templates
categoryOrder: 4
url_path: '/audit/templates/detailed'
title: 'Get audit templates detailed list'
type: 'GET'
order: 4
layout: null
---

Retrieve a detailed, paginated list of audit templates available in your MonitorQA system. This endpoint provides comprehensive template information with filtering and search capabilities.

## Query Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| templateType | integer | No | Filter templates by type |
| search | string | No | Filter templates by name (partial match) |
| pageNumber | integer | No | Page number for pagination (starts from 1) |
| pageSize | integer | No | Number of items per page |

### Example Request

```http
GET /audit/templates/detailed?search=safety&pageNumber=1&pageSize=10
Host: api-external.monitorqa.com
X-API-KEY: abcdef12345
```

## Response

**Success Response**

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "data": [
    {
      "id": "567890ab-cdef-1234-5678-90abcdef1234",
      "name": "Safety Inspection Template",
      "templateType": 0
    },
    {
      "id": "678901bc-defa-2345-6789-01bcdef12345",
      "name": "Equipment Safety Check",
      "templateType": 1
    }
  ],
  "meta": {
    "pageNumber": 1,
    "pageSize": 10,
    "totalCount": 25
  }
}
```

For errors responses, see the [response status codes documentation](#/response-status-codes).
