---
category: 12. Roles
url_path: '/roles'
title: 'Create Role'
type: 'POST'
order: 3
layout: null
---

Create a new role within a company. This endpoint enables defining custom roles with specific permissions for any role type (Admin, Auditor, Auditee, or Observer).

## Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| roleType | int | Yes | The type of role. Values: `0` (Admin), `1` (Auditor), `2` (Auditee), `3` (Observer) |
| name | string | Yes | The name of the role |
| description | string | No | A description of the role |
| permissions | array | No | Array of permission strings. All permissions in the array will be enabled. If not provided, the role will be created without permissions |
| permissions[] | string | Yes | The permission string constant (e.g., `audits.do`, `users.manage`). Must be valid for the specified role type. See [Role Permissions Reference](#/roles/permissions) for detailed descriptions |

### Role Types

- `0` - Admin
- `1` - Auditor
- `2` - Auditee
- `3` - Observer

### Example Request - Admin Role

```http
POST /roles
Host: api-external.monitorqa.com
X-API-KEY: abcdef12345
Content-Type: application/json

{
  "roleType": 0,
  "name": "System Administrator",
  "description": "Full system administrator with all permissions",
  "permissions": ["audits.do", "audits.viewResults", "users.manage", "roles.manage"]
}
```

### Example Request - Auditor Role

```http
POST /roles
Host: api-external.monitorqa.com
X-API-KEY: abcdef12345
Content-Type: application/json

{
  "roleType": 1,
  "name": "Senior Quality Auditor",
  "description": "Senior auditor with expanded permissions for quality management",
  "permissions": ["audits.do", "audits.viewResults", "issues.view"]
}
```

### Example Request - Auditee Role

```http
POST /roles
Host: api-external.monitorqa.com
X-API-KEY: abcdef12345
Content-Type: application/json

{
  "roleType": 2,
  "name": "Department Auditee",
  "description": "Department representative for audit responses and corrective actions",
  "permissions": ["audits.viewResults", "correctiveActions.do", "correctiveActions.view"]
}
```

### Example Request - Observer Role

```http
POST /roles
Host: api-external.monitorqa.com
X-API-KEY: abcdef12345
Content-Type: application/json

{
  "roleType": 3,
  "name": "Quality Observer",
  "description": "Read-only access to audit results and reports",
  "permissions": ["audits.viewResults", "correctiveActions.view", "issues.view", "reports.viewSummary"]
}
```

### Example Request - Role Without Permissions

```http
POST /roles
Host: api-external.monitorqa.com
X-API-KEY: abcdef12345
Content-Type: application/json

{
  "roleType": 0,
  "name": "Basic Admin Role",
  "description": "Admin role without specific permissions"
}
```

## Response

**Success Response**

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "id": "123456ab-cdef-789a-bcde-f12345678901"
}
```

For errors responses, see the [response status codes documentation](#/response-status-codes).

## Validation Rules

The following validation rules are enforced when creating roles:

1. **Role Type**: Required and must be a valid role type (0-3)
2. **Role Name**: Required and cannot be empty
3. **Permissions**: Optional. If provided, permission strings must be valid permission constants for the specified role type. See [Role Permissions Reference](#/roles/permissions) for the complete list of available permissions for each role type

**Note**: Requests that violate these rules will return a 400 Bad Request with detailed validation error messages.

## Permission Guidelines

Each role type has its own set of available permissions:

- **Admin roles (roleType: 0)**: 31 permissions available, including full system control, user management, billing, and all operational permissions
- **Auditor roles (roleType: 1)**: 17 permissions available, focused on audit execution, issue management, corrective action oversight, and performance reporting
- **Auditee roles (roleType: 2)**: 4 permissions available, for viewing audit results, executing corrective actions, and limited object access
- **Observer roles (roleType: 3)**: 9 permissions available, providing read-only access to audits, issues, corrective actions, and all reports

For detailed descriptions of each permission, see the [Role Permissions Reference](#/roles/permissions).

