---
category: 7. Users
categoryOrder: 7
url_path: '/users/{id}'
title: 'Update user'
type: 'PUT'
order: 3
layout: null
---

Update an existing user's information within the company account. This endpoint enables modifying a user's name, role, and phone number while preserving other account details.

## Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| id | string | Yes | The unique identifier of the user to update |
| fullName | string | Yes | The user's full name |
| roleId | string | No | The ID of the role to assign to the user (if not specified, role remains unchanged) |
| phone | string | No | The user's phone number (max 50 characters) |

### Example Request

```http
PUT /users/123e4567-e89b-12d3-a456-426614174000
Host: api-external.monitorqa.com
X-API-KEY: abcdef12345
Content-Type: application/json

{
  "fullName": "John David Smith",
  "roleId": "456e7890-e89b-12d3-a456-426614174000",
  "phone": "+1-555-0123"
}
```

## Response

**Success Response**

```http
HTTP/1.1 200 OK
```

Empty response body indicates successful user update.

For errors responses, see the [response status codes documentation](#/response-status-codes).
