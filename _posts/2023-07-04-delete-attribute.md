---
category: Audit object attributes
categoryOrder: 6
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

### Example Request

```http
DELETE /audit/objects/attributes
Host: api-external.monitorqa.com
X-API-KEY: abcdef12345
Content-Type: application/json

{
  "ids": [
    "890123de-fghi-4567-890a-bcdef1234567",
    "901234ef-ghij-5678-90ab-cdef12345678",
    "012345fg-hijk-6789-01bc-def123456789"
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
