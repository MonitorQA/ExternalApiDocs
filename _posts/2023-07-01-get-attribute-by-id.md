---
category: 10. Audit Object Attributes
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

## Request Example

```http
GET https://api-external.monitorqa.com/audit/objects/attributes/{id}
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
      "id": "option-123"
    },
    {
      "isDefault": false,
      "name": "Medium Priority",
      "id": "option-456"
    },
    {
      "isDefault": false,
      "name": "Low Priority",
      "id": "option-789"
    }
  ],
  "name": "Priority Level",
  "id": "attr-priority-001"
}
```

For errors responses, see the [response status codes documentation](#/response-status-codes).
