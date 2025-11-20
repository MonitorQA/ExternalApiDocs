---
category: 9. Roles
categoryOrder: 9
title: 'Role Permissions Reference'
order: 1
layout: null
---

This reference document provides detailed descriptions of all available permissions for each role type in the MonitorQA system. Permissions use Google IAM-style string constants (e.g., `audits.do`, `audits.manage`). Use this reference when configuring role permissions through the Create Role and Update Role endpoints.

## Admin Role Permissions (roleType: 0)

Admin roles have access to all system permissions, providing complete control over the MonitorQA platform.

| Permission String | Description |
|-------------------|-------------|
| `audits.do` | Ability to perform and complete audits as an auditor |
| `audits.assign` | Authority to assign audits to other users and manage audit assignments |
| `audits.manage` | Full management capabilities for audits including creation, modification, and deletion |
| `audits.schedule` | Permission to create and manage audit schedules and recurring audit plans |
| `audits.createInstant` | Ability to create immediate, unscheduled audits for urgent situations |
| `audits.viewResults` | Access to view completed audit results, findings, and outcomes |
| `correctiveActions.manage` | Full management of corrective actions including creation, assignment, and tracking |
| `correctiveActions.approve` | Authority to approve or reject proposed corrective actions |
| `correctiveActions.assign` | Permission to assign corrective actions to responsible parties |
| `correctiveActions.do` | Ability to execute and complete assigned corrective actions |
| `correctiveActions.view` | Access to view corrective action details, status, and progress |
| `auditObjects.manage` | Full management of audit objects (locations, equipment, processes being audited) |
| `auditTemplates.manage` | Authority to create, modify, and delete audit templates and question sets |
| `users.manage` | Complete user management including creation, modification, role assignment, and deactivation |
| `tags.manage` | Management of tags used for categorizing and organizing audits and objects |
| `roles.manage` | Authority to create, modify, and delete user roles and their permissions |
| `scoreSystems.manage` | Management of scoring systems and criteria used in audit evaluations |
| `billing.manage` | Access to billing information, subscription management, and payment settings |
| `generalSetup.manage` | Authority to modify system-wide settings and general configuration |
| `auditObjects.accessNonParticipant` | Ability to access and audit objects even when not directly assigned as a participant |
| `issueTypes.manage` | Management of issue types and categories used in audit findings |
| `issues.delete` | Authority to permanently delete issues identified during audits |
| `issues.edit` | Permission to modify existing issues, their details, and categorization |
| `issues.changeStatus` | Ability to update the status of issues (open, in progress, resolved, etc.) |
| `issues.view` | Access to view issues identified during audits and their current status |
| `reports.viewSummary` | Access to high-level summary reports and dashboard analytics |
| `reports.viewAuditPerformance` | Detailed reports on audit performance metrics and completion rates |
| `reports.viewAuditorPerformance` | Performance analytics for individual auditors and their effectiveness |
| `reports.viewAuditObjectPerformance` | Performance reports for specific audit objects and their compliance history |
| `reports.viewItemAnalysis` | Detailed analysis reports on specific audit items and question performance |
| `dataExports.accessCustom` | Permission to export custom data sets and create specialized reports |

## Auditor Role Permissions (roleType: 1)

Auditor roles are designed for users who primarily conduct audits and manage audit-related activities.

| Permission String | Description |
|-------------------|-------------|
| `audits.do` | Ability to perform and complete audits as an auditor |
| `audits.assign` | Authority to assign audits to other users and manage audit assignments |
| `audits.createInstant` | Ability to create immediate, unscheduled audits for urgent situations |
| `audits.viewResults` | Access to view completed audit results, findings, and outcomes |
| `correctiveActions.approve` | Authority to approve or reject proposed corrective actions |
| `correctiveActions.assign` | Permission to assign corrective actions to responsible parties |
| `correctiveActions.do` | Ability to execute and complete assigned corrective actions |
| `correctiveActions.view` | Access to view corrective action details, status, and progress |
| `auditObjects.accessNonParticipant` | Ability to access and audit objects even when not directly assigned as a participant |
| `issues.edit` | Permission to modify existing issues, their details, and categorization |
| `issues.changeStatus` | Ability to update the status of issues (open, in progress, resolved, etc.) |
| `issues.view` | Access to view issues identified during audits and their current status |
| `reports.viewSummary` | Access to high-level summary reports and dashboard analytics |
| `reports.viewAuditPerformance` | Detailed reports on audit performance metrics and completion rates |
| `reports.viewAuditorPerformance` | Performance analytics for individual auditors and their effectiveness |
| `reports.viewAuditObjectPerformance` | Performance reports for specific audit objects and their compliance history |
| `reports.viewItemAnalysis` | Detailed analysis reports on specific audit items and question performance |

## Auditee Role Permissions (roleType: 2)

Auditee roles are for users who are subject to audits and responsible for responding to findings and implementing corrective actions.

| Permission String | Description |
|-------------------|-------------|
| `audits.viewResults` | Access to view completed audit results, findings, and outcomes relevant to their area |
| `correctiveActions.do` | Ability to execute and complete assigned corrective actions |
| `correctiveActions.view` | Access to view corrective action details, status, and progress for their assigned actions |
| `auditObjects.accessNonParticipant` | Limited ability to access audit objects outside their direct responsibility when relevant |

## Observer Role Permissions (roleType: 3)

Observer roles provide read-only access to audit information and reports, suitable for stakeholders who need visibility without operational involvement.

| Permission String | Description |
|-------------------|-------------|
| `audits.viewResults` | Access to view completed audit results, findings, and outcomes |
| `correctiveActions.view` | Access to view corrective action details, status, and progress |
| `auditObjects.accessNonParticipant` | Ability to view audit objects and their information for monitoring purposes |
| `issues.view` | Access to view issues identified during audits and their current status |
| `reports.viewSummary` | Access to high-level summary reports and dashboard analytics |
| `reports.viewAuditPerformance` | Detailed reports on audit performance metrics and completion rates |
| `reports.viewAuditorPerformance` | Performance analytics for individual auditors and their effectiveness |
| `reports.viewAuditObjectPerformance` | Performance reports for specific audit objects and their compliance history |
| `reports.viewItemAnalysis` | Detailed analysis reports on specific audit items and question performance |

## Usage Notes

- **Permission Format**: Permissions use Google IAM-style string constants with dot notation (e.g., `audits.do`, `users.manage`)
- **Permission Hierarchy**: Admin roles include all permissions available to other role types, plus additional management capabilities
- **Role-Specific Permissions**: Each role type has its own set of available permissions. Use only permissions valid for the specific role type
- **Conditional Access**: Some permissions may have additional business logic restrictions based on user assignments and object relationships
- **Scalability**: Observer roles are ideal for executives and stakeholders who need visibility without operational permissions
