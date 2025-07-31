---
category: 12. Roles
url_path: '/roles/{id}'
title: 'Update Role'
type: 'PUT'
order: 4
layout: null
---

Update an existing role within your company. This endpoint allows you to modify role details including name, description, permissions, and role type.

## URL Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| id | uuid | Yes | The unique identifier of the role to update |

## Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| name | string | Yes | The name of the role |
| description | string | No | A description of the role |
| roleType | int | Yes | The type of role. Values: `0` (Admin), `1` (Auditor), `2` (Auditee), `3` (Observer) |
| adminPermissions | array | Conditional | Array of admin permission objects. **Required when roleType = 0, must be null for other role types** |
| auditorPermissions | array | Conditional | Array of auditor permission objects. **Required when roleType = 1, must be null for other role types** |
| auditeePermissions | array | Conditional | Array of auditee permission objects. **Required when roleType = 2, must be null for other role types** |
| observerPermissions | array | Conditional | Array of observer permission objects. **Required when roleType = 3, must be null for other role types** |
| permissions[].isEnabled | boolean | Yes | Whether the permission is enabled |
| permissions[].permissionType | int | Yes | The permission type ID from the role-specific enum (see Permission Types below) |

### Example Request - Admin Role

```http
PUT /roles/123456ab-cdef-789a-bcde-f12345678901
Host: api-external.monitorqa.com
X-API-KEY: abcdef12345
Content-Type: application/json

{
  "name": "Updated System Administrator",
  "description": "Updated description for system administrator role",
  "roleType": 0,
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
PUT /roles/123456ab-cdef-789a-bcde-f12345678901
Host: api-external.monitorqa.com
X-API-KEY: abcdef12345
Content-Type: application/json

{
  "name": "Updated Senior Quality Auditor",
  "description": "Updated description for senior auditor role",
  "roleType": 1,
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
      "isEnabled": false,
      "permissionType": 11
    }
  ]
}
```

### Example Request - Auditee Role

```http
PUT /roles/234567bc-defg-890b-cdef-123456789012
Host: api-external.monitorqa.com
X-API-KEY: abcdef12345
Content-Type: application/json

{
  "name": "Updated Department Auditee",
  "description": "Updated department representative for audit responses",
  "roleType": 2,
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
      "isEnabled": true,
      "permissionType": 3
    }
  ]
}
```

### Example Request - Observer Role

```http
PUT /roles/345678cd-efgh-901c-def1-234567890123
Host: api-external.monitorqa.com
X-API-KEY: abcdef12345
Content-Type: application/json

{
  "name": "Updated Quality Observer",
  "description": "Updated read-only access to audit results and reports",
  "roleType": 3,
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
      "isEnabled": false,
      "permissionType": 2
    },
    {
      "isEnabled": true,
      "permissionType": 4
    },
    {
      "isEnabled": true,
      "permissionType": 5
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
```

For errors responses, see the [response status codes documentation](#/response-status-codes).

## Validation Rules

The following validation rules are enforced when updating roles:

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