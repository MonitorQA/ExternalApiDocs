---
category: 7. Users
url_path: '/users'
title: 'Delete users'
type: 'DELETE'
order: 26
layout: null
---

Delete multiple users from your company account. This endpoint allows you to remove users in bulk by providing an array of user IDs. Use caution as this action cannot be undone.

## Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| ids | array[string] | Yes | Array of user IDs to be deleted |

## Request Example

```http
DELETE https://api-external.monitorqa.com/users
X-API-KEY: abcdef12345
Content-Type: application/json

{
  "ids": [
    "user-123",
    "user-456",
    "user-789"
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
