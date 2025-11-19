---
category: 2. Audits
url_path: '/audit/expire'
type: 'POST'
order: 2
layout: null
---

Manually expire incomplete audits in the organization. This endpoint enables marking multiple audits as expired, effectively closing them without completion. This is useful for audits that are no longer relevant or cannot be completed.

## Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| ids | array[string] | Yes | Array of audit IDs to be expired |

### Example Request

```http
POST /audit/expire
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

Empty response body indicates successful expiration of specified audits.


For errors responses, see the [response status codes documentation](#/response-status-codes).
