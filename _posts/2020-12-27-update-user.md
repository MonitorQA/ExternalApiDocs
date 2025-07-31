---
category: 7. Users
url_path: '/users/{id}'
title: 'Update user'
type: 'PUT'
order: 25
layout: null
---

Update an existing user's information within your company account. This endpoint allows you to modify a user's name, role, and phone number while preserving other account details.

## Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| id | string | Yes | The unique identifier of the user to update |
| fullName | string | Yes | The user's full name |
| roleId | string | No | The ID of the role to assign to the user (if not specified, role remains unchanged) |
| phone | string | No | The user's phone number (max 50 characters) |

## Request Example

```http
PUT https://api-external.monitorqa.com/users/{id}
X-API-KEY: abcdef12345
Content-Type: application/json

{
  "fullName": "John David Smith",
  "roleId": "role-manager-123",
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
