---
category: Audits
categoryOrder: 2
url_path: '/audit/expire'
title: 'Expire audits'
type: 'POST'
order: 2
layout: null
---

Manually expire incomplete audits in the organization. This endpoint enables marking multiple audits as expired, effectively closing them without completion. This is useful for audits that are no longer relevant or cannot be completed.

### Request Headers

| Header | Type | Required | Description |
|--------|------|----------|-------------|
| `X-API-KEY` | string | Yes | API authentication key |
| `Content-Type` | string | Yes | Must be `application/json` |

### Request Body Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `ids` | array[uuid] | Yes | Array of audit IDs to be expired |

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


For error responses, see the [response status codes documentation](#/response-status-codes).
