---
category: 2. Audits
url_path: '/audit'
title: 'Delete Audit'
type: 'DELETE'
order: 25
layout: null
---

Delete multiple audits from your organization. This endpoint allows you to permanently remove audits in bulk by providing an array of audit IDs. Use with caution as this action cannot be undone.

## Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| ids | array[string] | Yes | Array of audit IDs to be deleted |

## Request Example

```http
DELETE https://api-external.monitorqa.com/audit
X-API-KEY: abcdef12345
Content-Type: application/json

{
  "ids": [
    "audit-123",
    "audit-456",
    "audit-789"
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
