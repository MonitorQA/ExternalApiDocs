---
category: 2. Audits
url_path: '/audit/expire'
title: 'Expire Audit'
type: 'POST'
order: 24
layout: null
---

Manually expire incomplete audits in your organization. This endpoint allows you to mark multiple audits as expired, effectively closing them without completion. This is useful for audits that are no longer relevant or cannot be completed.

## Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| ids | array[string] | Yes | Array of audit IDs to be expired |

## Request Example

```http
POST https://api-external.monitorqa.com/audit/expire
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

Empty response body indicates successful expiration of specified audits.


For errors responses, see the [response status codes documentation](#/response-status-codes).
