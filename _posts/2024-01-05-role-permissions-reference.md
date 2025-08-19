---
category: 12. Roles
title: 'Role Permissions Reference'
order: 0
layout: null
---

This reference document provides detailed descriptions of all available permissions for each role type in the MonitorQA system. Use this reference when configuring role permissions through the Create Role and Update Role endpoints.

## Admin Role Permissions (roleType: 0)

Admin roles have access to all system permissions, providing complete control over the MonitorQA platform.

| Permission ID | Permission Type | Description |
|---------------|-----------------|-------------|
| `0` | CanDoAudits | Ability to perform and complete audits as an auditor |
| `1` | CanAssignAudits | Authority to assign audits to other users and manage audit assignments |
| `2` | CanManageAudits | Full management capabilities for audits including creation, modification, and deletion |
| `3` | CanScheduleAudits | Permission to create and manage audit schedules and recurring audit plans |
| `4` | CanCreateInstantAudits | Ability to create immediate, unscheduled audits for urgent situations |
| `5` | CanViewAuditsResults | Access to view completed audit results, findings, and outcomes |
| `6` | CanManageCorrectiveActions | Full management of corrective actions including creation, assignment, and tracking |
| `7` | CanApproveCorrectiveActions | Authority to approve or reject proposed corrective actions |
| `8` | CanAssignCorrectiveActions | Permission to assign corrective actions to responsible parties |
| `9` | CanDoCorrectiveActions | Ability to execute and complete assigned corrective actions |
| `10` | CanViewCorrectiveActions | Access to view corrective action details, status, and progress |
| `11` | CanManageAuditObjects | Full management of audit objects (locations, equipment, processes being audited) |
| `12` | CanManageAuditTemplates | Authority to create, modify, and delete audit templates and question sets |
| `13` | CanManageUsers | Complete user management including creation, modification, role assignment, and deactivation |
| `14` | CanManageTags | Management of tags used for categorizing and organizing audits and objects |
| `15` | CanManageRoles | Authority to create, modify, and delete user roles and their permissions |
| `16` | CanManageScoreSystems | Management of scoring systems and criteria used in audit evaluations |
| `17` | CanManageBilling | Access to billing information, subscription management, and payment settings |
| `18` | CanManageGeneralSetup | Authority to modify system-wide settings and general configuration |
| `19` | CanAccessNonParticipantAuditObject | Ability to access and audit objects even when not directly assigned as a participant |
| `20` | CanManageIssueTypes | Management of issue types and categories used in audit findings |
| `21` | CanDeleteIssues | Authority to permanently delete issues identified during audits |
| `22` | CanEditIssues | Permission to modify existing issues, their details, and categorization |
| `23` | CanChangeIssuesStatus | Ability to update the status of issues (open, in progress, resolved, etc.) |
| `24` | CanViewIssues | Access to view issues identified during audits and their current status |
| `25` | CanViewSummaryReports | Access to high-level summary reports and dashboard analytics |
| `26` | CanViewAuditPerformanceReports | Detailed reports on audit performance metrics and completion rates |
| `27` | CanViewAuditorPerformanceReports | Performance analytics for individual auditors and their effectiveness |
| `28` | CanViewAuditObjectPerformanceReports | Performance reports for specific audit objects and their compliance history |
| `29` | CanViewItemAnalysisReports | Detailed analysis reports on specific audit items and question performance |
| `30` | CanAccessCustomDataExports | Permission to export custom data sets and create specialized reports |

## Auditor Role Permissions (roleType: 1)

Auditor roles are designed for users who primarily conduct audits and manage audit-related activities.

| Permission ID | Permission Type | Description |
|---------------|-----------------|-------------|
| `0` | CanDoAudits | Ability to perform and complete audits as an auditor |
| `1` | CanAssignAudits | Authority to assign audits to other users and manage audit assignments |
| `2` | CanCreateInstantAudits | Ability to create immediate, unscheduled audits for urgent situations |
| `3` | CanViewAuditsResults | Access to view completed audit results, findings, and outcomes |
| `4` | CanApproveCorrectiveActions | Authority to approve or reject proposed corrective actions |
| `5` | CanAssignCorrectiveActions | Permission to assign corrective actions to responsible parties |
| `6` | CanDoCorrectiveActions | Ability to execute and complete assigned corrective actions |
| `7` | CanViewCorrectiveActions | Access to view corrective action details, status, and progress |
| `8` | CanAccessNonParticipantAuditObject | Ability to access and audit objects even when not directly assigned as a participant |
| `9` | CanEditIssues | Permission to modify existing issues, their details, and categorization |
| `10` | CanChangeIssuesStatus | Ability to update the status of issues (open, in progress, resolved, etc.) |
| `11` | CanViewIssues | Access to view issues identified during audits and their current status |
| `12` | CanViewSummaryReports | Access to high-level summary reports and dashboard analytics |
| `13` | CanViewAuditPerformanceReports | Detailed reports on audit performance metrics and completion rates |
| `14` | CanViewAuditorPerformanceReports | Performance analytics for individual auditors and their effectiveness |
| `15` | CanViewAuditObjectPerformanceReports | Performance reports for specific audit objects and their compliance history |
| `16` | CanViewItemAnalysisReports | Detailed analysis reports on specific audit items and question performance |

## Auditee Role Permissions (roleType: 2)

Auditee roles are for users who are subject to audits and responsible for responding to findings and implementing corrective actions.

| Permission ID | Permission Type | Description |
|---------------|-----------------|-------------|
| `0` | CanViewAuditsResults | Access to view completed audit results, findings, and outcomes relevant to their area |
| `1` | CanDoCorrectiveActions | Ability to execute and complete assigned corrective actions |
| `2` | CanViewCorrectiveActions | Access to view corrective action details, status, and progress for their assigned actions |
| `3` | CanAccessNonParticipantAuditObject | Limited ability to access audit objects outside their direct responsibility when relevant |

## Observer Role Permissions (roleType: 3)

Observer roles provide read-only access to audit information and reports, suitable for stakeholders who need visibility without operational involvement.

| Permission ID | Permission Type | Description |
|---------------|-----------------|-------------|
| `0` | CanViewAuditsResults | Access to view completed audit results, findings, and outcomes |
| `1` | CanViewCorrectiveActions | Access to view corrective action details, status, and progress |
| `2` | CanAccessNonParticipantAuditObject | Ability to view audit objects and their information for monitoring purposes |
| `3` | CanViewIssues | Access to view issues identified during audits and their current status |
| `4` | CanViewSummaryReports | Access to high-level summary reports and dashboard analytics |
| `5` | CanViewAuditPerformanceReports | Detailed reports on audit performance metrics and completion rates |
| `6` | CanViewAuditorPerformanceReports | Performance analytics for individual auditors and their effectiveness |
| `7` | CanViewAuditObjectPerformanceReports | Performance reports for specific audit objects and their compliance history |
| `8` | CanViewItemAnalysisReports | Detailed analysis reports on specific audit items and question performance |

## Usage Notes

- **Permission Hierarchy**: Admin roles include all permissions available to other role types, plus additional management capabilities
- **Role-Specific Enums**: Each role type uses its own permission enumeration starting from 0
- **Conditional Access**: Some permissions may have additional business logic restrictions based on user assignments and object relationships
- **Scalability**: Observer roles are ideal for executives and stakeholders who need visibility without operational permissions