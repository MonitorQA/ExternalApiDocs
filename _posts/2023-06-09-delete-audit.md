---
category: Audits
categoryOrder: 2
url_path: '/audit'
title: 'Delete Audit'
type: 'DELETE'
order: 2
layout: null
---

Delete multiple audits from the organization. This endpoint enables permanently removing audits in bulk by providing an array of audit IDs. Use with caution as this action cannot be undone.

## Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| ids | array[string] | Yes | Array of audit IDs to be deleted |

### Example Request

```http
DELETE /audit
Host: api-external.monitorqa.com
X-API-KEY: abcdef12345
Content-Type: application/json

{
  "ids": [
    "123e4567-e89b-12d3-a456-426614174000",
    "456e7890-e89b-12d3-a456-426614174000",
    "789e0123-e89b-12d3-a456-426614174000"
  ]
}
```

## Response

**Success Response**

```http
HTTP/1.1 200 OK
```

Empty response body indicates successful deletion of specified audits.


For errors responses, see the [response status codes documentation](#/response-status-codes).
