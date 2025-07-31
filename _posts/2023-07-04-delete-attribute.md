---
category: 10. Audit Object Attributes
url_path: '/audit/objects/attributes'
title: 'Delete Audit Object Attribute'
type: 'DELETE'
order: 5
layout: null
---

Delete multiple audit object attributes permanently. This endpoint removes attributes and all associated audit object assignments. Use with caution as this action cannot be undone.

## Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| ids | array[string] | Yes | Array of audit object attribute IDs to be deleted |

## Request Example

```http
DELETE https://api-external.monitorqa.com/audit/objects/attributes
X-API-KEY: abcdef12345
Content-Type: application/json

{
  "ids": [
    "attr-dept-001",
    "attr-priority-001",
    "attr-location-001"
  ]
}
```

## Response

**Success Response**

```http
HTTP/1.1 200 OK
```

Empty response body indicates successful deletion of specified attributes and their assignments.

For errors responses, see the [response status codes documentation](#/response-status-codes).
