---
category: Roles
categoryOrder: 9
url_path: '/roles'
title: 'Delete Roles'
type: 'DELETE'
order: 6
layout: null
---

Delete one or multiple roles from your company. This endpoint accepts an array of role IDs to delete multiple roles in a single request.

### Request Headers

| Header | Type | Required | Description |
|--------|------|----------|-------------|
| `X-API-KEY` | string | Yes | API authentication key |
| `Content-Type` | string | Yes | Must be `application/json` |

### Request Body Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `ids` | uuid[] | Yes | Array of role IDs to delete |

### Example Request

```http
DELETE /roles
Host: api-external.monitorqa.com
X-API-KEY: abcdef12345
Content-Type: application/json

{
  "ids": [
    "123456ab-cdef-789a-bcde-f12345678901",
    "234567bc-def0-890b-cdef-123456789012",
    "345678cd-ef00-901c-def1-234567890123"
  ]
}
```

### Single Role Deletion

```http
DELETE /roles
Host: api-external.monitorqa.com
X-API-KEY: abcdef12345
Content-Type: application/json

{
  "ids": [
    "123456ab-cdef-789a-bcde-f12345678901"
  ]
}
```

## Response

**Success Response**

```http
HTTP/1.1 200 OK
Content-Type: application/json
```

For error responses, see the [response status codes documentation](#/response-status-codes).