---
category: 6. User Groups
url_path: '/user-groups'
title: 'Get list of user groups'
type: 'GET'
order: 22
layout: null
---

Retrieve a list of all user groups within your company. This endpoint provides the basic identification information for user groups, which can be used for audit assignments and access management.

### Example Request

```http
GET /user-groups
Host: api-external.monitorqa.com
X-API-KEY: abcdef12345
```

## Response

**Success Response**

```http
HTTP/1.1 200 OK
Content-Type: application/json

[
  {
    "id": "123456gh-ijkl-789a-bcde-f12345678901",
    "name": "Safety Inspectors"
  },
  {
    "id": "234567hi-jklm-890a-bcde-f12345678902",
    "name": "Quality Assurance Team"
  },
  {
    "id": "345678ij-klmn-901a-bcde-f12345678903",
    "name": "Maintenance Supervisors"
  }
]
```

For errors responses, see the [response status codes documentation](#/response-status-codes).
