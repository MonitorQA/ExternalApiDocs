---
category: Users
url_path: '/users/have-permission/{permissionType}'
title: 'Filter users by permission'
type: 'POST'

layout: null
---

This method allows to filter given list of user ids by role permission.

### Request

* The headers must include a **valid api key**.

* **permissionType** parameter might have following value:
  * CanDoAudits = 1,
  * CanAssignAudits = 2,
  * CanManageAudits = 3,
  * CanScheduleAudits = 4,
  * CanCreateInstantAudits = 5,
  * CanViewAuditResults = 6,
  * CanManageCorrectiveActions = 7,
  * CanApproveCorrectiveActions = 9,
  * CanAssignCorrectiveActions = 10,
  * CanDoCorrectiveActions = 11,
  * CanViewCorrectiveActions = 12,
  * CanViewAnalytics = 13,
  * CanManageAuditObjects = 15,
  * CanManageAuditTemplates = 16,
  * CanManageUsers = 17,
  * CanManageTags = 18,
  * CanManageRoles = 19,
  * CanManageScoreSystems = 20,
  * CanManageBilling = 21,
  * CanManageGeneralSetup = 23,
  * CanAccessNonParticipantAuditObject = 24

* The body must include array of user ids.


```X-API-KEY:  abcdef12345```

```[
    "string"
]```

### Response

Returns a collection of company users from posted list with role permission enabled.

```Status: 200 OK```
```[
  {
    "id": "string",
    "name": "string",
    "email": "string"
  }
]```

For errors responses, see the [response status codes documentation](#/response-status-codes).
