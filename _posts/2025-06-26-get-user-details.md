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
  "role": {
    "id": "456e7890-e89b-12d3-a456-426614174001",
    "name": "Senior Auditor",
    "roleType": 1
  }
}
```

### Response Fields

| Field | Type | Description |
|-------|------|-------------|
| `id` | uuid | The unique identifier of the user |
| `name` | string | The user's full name |
| `email` | string | The user's email address |
| `role` | object | The user's role information |
| `role.id` | uuid | The unique identifier of the role |
| `role.name` | string | The role name |
| `role.roleType` | number | The role type. Values: `0` (Admin), `1` (Auditor), `2` (Auditee), `3` (Observer) |

For errors responses, see the [response status codes documentation](#/response-status-codes).

