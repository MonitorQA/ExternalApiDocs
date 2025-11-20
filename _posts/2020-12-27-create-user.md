---
category: 7. Users
categoryOrder: 7
url_path: '/users'
title: 'Create user'
type: 'POST'
order: 2
layout: null
---

Create a new user within the company. The user will receive an invitation email to set up their account and access the MonitorQA platform.

### Request Headers

| Header | Type | Required | Description |
|--------|------|----------|-------------|
| `X-API-KEY` | string | Yes | API authentication key |

### Request Body Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `email` | string | Yes | User's email address (must be unique within the company) |
| `fullName` | string | Yes | User's full name for display purposes |
| `roleId` | string | Yes | Unique identifier of the role to assign to the user |
| `phone` | string | No | User's phone number (maximum 50 characters) |

### Example Request

```http
POST /users
Host: api-external.monitorqa.com
X-API-KEY: abcdef12345
Content-Type: application/json

{
  "fullName": "John Smith", 
  "email": "john.smith@company.com",
  "roleId": "123e4567-e89b-12d3-a456-426614174000",
  "phone": "+1-555-123-4567"
}
```

## Response

**Success Response**

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "id": "a1b2c3d4-e5f6-789a-bcde-f01234567890"   
}
```

For errors responses, see the [response status codes documentation](#/response-status-codes).
