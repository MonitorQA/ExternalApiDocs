---
category: Users
categoryOrder: 7
url_path: '/users/{id}'
title: 'Get user details'
type: 'GET'
order: 2
layout: null
---

Retrieve detailed information about a specific user by their unique identifier. This endpoint provides comprehensive user information including role, permissions, and account details.

### Request Headers

| Header | Type | Required | Description |
|--------|------|----------|-------------|
| `X-API-KEY` | string | Yes | API authentication key |

### Path Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `id` | uuid | Yes | The unique identifier of the user |

### Example Request

```http
GET /users/123e4567-e89b-12d3-a456-426614174000
Host: api-external.monitorqa.com
X-API-KEY: abcdef12345
```

## Response

**Success Response**

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "id": "123e4567-e89b-12d3-a456-426614174000",
  "name": "John Smith",
  "email": "john.smith@company.com",
  "phone": "+1-555-0123",
  "role": {
    "id": "456e7890-e89b-12d3-a456-426614174001",
    "name": "Senior Auditor",
    "roleType": 1
  },
  "userGroups": [
    {
      "id": "789e0123-e89b-12d3-a456-426614174002",
      "name": "Warehouse Auditors"
    }
  ]
}
```

### Response Fields

| Field | Type | Description |
|-------|------|-------------|
| `id` | uuid | The unique identifier of the user |
| `name` | string | The user's full name |
| `email` | string | The user's email address |
| `phone` | string | Optional. The user's phone number |
| `role` | object | Optional. The user's role. Contains `id` (uuid), `name` (string), and `roleType` (number) |
| `role.id` | uuid | The unique identifier of the role |
| `role.name` | string | The role name |
| `role.roleType` | number | The role type. See [Role Types](#role-types) below |
| `userGroups` | array | The user groups the user belongs to. Each item has `id` (uuid) and `name` (string) |
| `userGroups[].id` | uuid | The unique identifier of the user group |
| `userGroups[].name` | string | The user group name |

### Role Types

| Value | Role Type |
|-------|-----------|
| `0` | Admin |
| `1` | Auditor |
| `2` | Auditee |
| `3` | Observer |

For full role types and permissions details, see the [Role Permissions Reference](#/role-permissions-reference).

For errors responses, see the [response status codes documentation](#/response-status-codes).

