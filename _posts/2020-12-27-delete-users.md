---
category: 7. Users
categoryOrder: 7
url_path: '/users'
title: 'Delete users'
type: 'DELETE'
order: 4
layout: null
---

Delete multiple users from the company account. This endpoint enables removing users in bulk by providing an array of user IDs. Use caution as this action cannot be undone.

## Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| ids | array[string] | Yes | Array of user IDs to be deleted |

### Example Request

```http
DELETE /users
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

Empty response body indicates successful deletion of specified users.

For errors responses, see the [response status codes documentation](#/response-status-codes).
