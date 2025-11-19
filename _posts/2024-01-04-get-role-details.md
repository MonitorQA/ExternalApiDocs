---
category: 9. Roles
url_path: '/roles/{id}'
title: 'Get Role Details'
type: 'GET'
order: 1
layout: null
---

Retrieve detailed information about a specific role within a company. This endpoint provides complete role information including ID, name, description, role type, and all enabled permissions.

## Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| id | Guid | Yes | The unique identifier of the role (path parameter) |

### Example Request

```http
GET /roles/123456ab-cdef-789a-bcde-f12345678901
Host: api-external.monitorqa.com
X-API-KEY: abcdef12345
```

## Response

**Success Response**

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "id": "123456ab-cdef-789a-bcde-f12345678901",
  "name": "System Administrator",
  "description": "Full system administrator with all permissions",
  "roleType": 0,
  "permissions": ["audits.do", "audits.viewResults", "auditObjects.accessNonParticipant", "reports.viewSummary", "dataExports.accessCustom"]
}
```

### Response Fields

| Field | Type | Description |
|-------|------|-------------|
| id | Guid | The unique identifier of the role |
| name | string | The name of the role |
| description | string | The description of the role |
| roleType | int | The type of role. Values: `0` (Admin), `1` (Auditor), `2` (Auditee), `3` (Observer) |
| permissions | array | Array of enabled permission string constants. The permission strings correspond to the role type (see [Role Permissions Reference](#/roles/permissions)) |

### Role Types

- `0` - Admin
- `1` - Auditor
- `2` - Auditee
- `3` - Observer

### Permission Strings

The permissions array contains string constants (Google IAM-style) that correspond to permissions for the role type:

- **Admin roles**: Use admin permission strings (e.g., `audits.do`, `users.manage`)
- **Auditor roles**: Use auditor permission strings (e.g., `audits.do`, `audits.viewResults`)
- **Auditee roles**: Use auditee permission strings (e.g., `audits.viewResults`, `correctiveActions.do`)
- **Observer roles**: Use observer permission strings (e.g., `audits.viewResults`, `reports.viewSummary`)

For detailed descriptions of each permission, see the [Role Permissions Reference](#/roles/permissions).

### Example Response - Admin Role

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "id": "123456ab-cdef-789a-bcde-f12345678901",
  "name": "System Administrator",
  "description": "Full system administrator with all permissions",
  "roleType": 0,
  "permissions": ["audits.do", "audits.assign", "audits.manage", "audits.viewResults", "users.manage", "roles.manage", "reports.viewSummary"]
}
```

### Example Response - Auditor Role

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "id": "234567hi-jklm-890a-bcde-f12345678902",
  "name": "Senior Quality Auditor",
  "description": "Senior auditor with expanded permissions",
  "roleType": 1,
  "permissions": ["audits.do", "audits.viewResults", "issues.view", "reports.viewSummary"]
}
```

### Example Response - Auditee Role

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "id": "345678ij-klmn-901a-bcde-f12345678903",
  "name": "Department Auditee",
  "description": "Department representative for audit responses",
  "roleType": 2,
  "permissions": ["audits.viewResults", "correctiveActions.do", "correctiveActions.view"]
}
```

### Example Response - Observer Role

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "id": "456789jk-lmno-012b-cdef-123456789012",
  "name": "Quality Observer",
  "description": "Read-only access to audit results and reports",
  "roleType": 3,
  "permissions": ["audits.viewResults", "correctiveActions.view", "issues.view", "reports.viewSummary"]
}
```

## Error Responses

**Role Not Found (404)**

```http
HTTP/1.1 404 Not Found
```

Returned when the specified role ID does not exist or does not belong to the company.

For errors responses, see the [response status codes documentation](#/response-status-codes).

