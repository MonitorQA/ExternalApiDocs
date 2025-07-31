---
category: 12. Roles
url_path: '/roles'
title: 'Create Role'
type: 'POST'
order: 3
layout: null
---

Create a new role within your company. This endpoint allows you to define custom roles with specific permissions and role types.

## Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| roleType | int | Yes | The type of role. Values: `0` (Admin), `1` (Auditor), `2` (Auditee), `3` (Observer) |
| name | string | Yes | The name of the role |
| description | string | No | A description of the role |
| adminPermissions | array | Conditional | Array of admin permission objects. **Required when roleType = 0, must be null for other role types** |
| auditorPermissions | array | Conditional | Array of auditor permission objects. **Required when roleType = 1, must be null for other role types** |
| auditeePermissions | array | Conditional | Array of auditee permission objects. **Required when roleType = 2, must be null for other role types** |
| observerPermissions | array | Conditional | Array of observer permission objects. **Required when roleType = 3, must be null for other role types** |
| permissions[].isEnabled | boolean | Yes | Whether the permission is enabled |
| permissions[].permissionType | int | Yes | The permission type ID from the role-specific enum (see Permission Types below) |

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
  "adminPermissions": [
    {
      "isEnabled": true,
      "permissionType": 0
    },
    {
      "isEnabled": true,
      "permissionType": 5
    },
    {
      "isEnabled": false,
      "permissionType": 19
    }
  ]
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
  "auditorPermissions": [
    {
      "isEnabled": true,
      "permissionType": 0
    },
    {
      "isEnabled": true,
      "permissionType": 3
    },
    {
      "isEnabled": true,
      "permissionType": 11
    }
  ]
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
  "auditeePermissions": [
    {
      "isEnabled": true,
      "permissionType": 0
    },
    {
      "isEnabled": true,
      "permissionType": 1
    },
    {
      "isEnabled": true,
      "permissionType": 2
    },
    {
      "isEnabled": false,
      "permissionType": 3
    }
  ]
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
  "observerPermissions": [
    {
      "isEnabled": true,
      "permissionType": 0
    },
    {
      "isEnabled": true,
      "permissionType": 1
    },
    {
      "isEnabled": true,
      "permissionType": 3
    },
    {
      "isEnabled": true,
      "permissionType": 4
    }
  ]
}
```

### Available Permissions by Role Type

**Note:** Each role type uses its own permission enum with sequential numbering starting from 0. Only the appropriate permission array should be populated based on the roleType.

For detailed descriptions of each permission type, see the [Role Permissions Reference](#/roles/permissions).

#### Permission Array Usage by Role Type

| Role Type | Role ID | Permission Array | Available Permissions |
|-----------|---------|------------------|----------------------|
| Admin | `0` | `adminPermissions` | 31 permissions (IDs 0-30) - Full system access |
| Auditor | `1` | `auditorPermissions` | 17 permissions (IDs 0-16) - Audit execution and management |
| Auditee | `2` | `auditeePermissions` | 4 permissions (IDs 0-3) - Response to audits and corrective actions |
| Observer | `3` | `observerPermissions` | 9 permissions (IDs 0-8) - Read-only access to reports and results |

**Quick Reference:**
- **Admin permissions (0-30)**: Complete system control including user management, billing, and all operational permissions
- **Auditor permissions (0-16)**: Audit execution, issue management, corrective action oversight, and performance reporting
- **Auditee permissions (0-3)**: View audit results, execute corrective actions, limited object access
- **Observer permissions (0-8)**: Read-only access to audits, issues, corrective actions, and all reports

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

1. **Role Name**: Required and cannot be empty
2. **Role Type**: Must be a valid enum value (0-3)
3. **Permission Array Validation**:
   - Exactly one permission array must be provided based on the role type
   - Other permission arrays must be null or omitted
   - The provided permission array must contain at least one permission
4. **Permission Type Validation**:
   - Permission types must be valid for the specified role type
   - Permission types must use the correct enum values (0-based sequential numbering)
5. **Role Type Mapping**:
   - Admin (0) → use `adminPermissions` only
   - Auditor (1) → use `auditorPermissions` only  
   - Auditee (2) → use `auditeePermissions` only
   - Observer (3) → use `observerPermissions` only

**Note**: Requests that violate these rules will return a 400 Bad Request with detailed validation error messages.