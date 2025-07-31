---
category: 6. User Groups
url_path: '/user-groups'
title: 'Get list of user groups'
type: 'GET'
order: 22
layout: null
---

Retrieve a list of all user groups within your company. This endpoint provides the basic identification information for user groups, which can be used for audit assignments and access management.

## Request Example

```http
GET https://api-external.monitorqa.com/user-groups
X-API-KEY: abcdef12345
```

## Response

**Success Response**

```http
HTTP/1.1 200 OK
Content-Type: application/json

[
  {
    "id": "group-123",
    "name": "Safety Inspectors"
  },
  {
    "id": "group-456",
    "name": "Quality Assurance Team"
  },
  {
    "id": "group-789",
    "name": "Maintenance Supervisors"
  }
]
```

For errors responses, see the [response status codes documentation](#/response-status-codes).
