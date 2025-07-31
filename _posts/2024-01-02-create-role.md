---
category: 12. Roles
url_path: '/roles'
title: 'Create Role'
type: 'POST'
order: 2
layout: null
---

Create a new role within your company. This endpoint allows you to define custom roles with specific permissions and role types.

## Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| roleType | int | Yes | The type of role. Values: `0` (Admin), `1` (Auditor), `2` (Auditee), `3` (Observer) |
| name | string | Yes | The name of the role |
| description | string | No | A description of the role |
| permissions | array | Yes | Array of permission objects |
| permissions[].isEnabled | boolean | Yes | Whether the permission is enabled |
| permissions[].rolePermissionType | int | Yes | The permission type ID (see Permission Types below) |

### Example Request

```http
POST /roles
Host: api-external.monitorqa.com
X-API-KEY: abcdef12345
Content-Type: application/json

{
  "roleType": 1,
  "name": "Senior Quality Auditor",
  "description": "Senior auditor with expanded permissions for quality management",
  "permissions": [
    {
      "isEnabled": true,
      "rolePermissionType": 1
    },
    {
      "isEnabled": true,
      "rolePermissionType": 6
    },
    {
      "isEnabled": true,
      "rolePermissionType": 28
    }
  ]
}
```

### Permission Types
- `1` - CanDoAudits
- `2` - CanAssignAudits
- `3` - CanManageAudits
- `4` - CanScheduleAudits
- `5` - CanCreateInstantAudits
- `6` - CanViewAuditsResults
- `7` - CanManageCorrectiveActions
- `9` - CanApproveCorrectiveActions
- `10` - CanAssignCorrectiveActions
- `11` - CanDoCorrectiveActions
- `12` - CanViewCorrectiveActions
- `15` - CanManageAuditObjects
- `16` - CanManageAuditTemplates
- `17` - CanManageUsers
- `18` - CanManageTags
- `19` - CanManageRoles
- `20` - CanManageScoreSystems
- `21` - CanManageBilling
- `23` - CanManageGeneralSetup
- `24` - CanAccessNonParticipantAuditObject
- `25` - CanDeleteIssues
- `26` - CanEditIssues
- `27` - CanChangeIssuesStatus
- `28` - CanViewIssues
- `29` - CanManageIssueTypes
- `30` - CanViewSummaryReports
- `31` - CanViewAuditPerformanceReports
- `32` - CanViewAuditorPerformanceReports
- `33` - CanViewAuditObjectPerformanceReports
- `34` - CanViewItemAnalysisReports
- `35` - CanAccessCustomDataExports

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