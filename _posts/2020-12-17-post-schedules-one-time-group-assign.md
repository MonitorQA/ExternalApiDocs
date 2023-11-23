---
category: Schedules
url_path: '/schedules/one-time/group-assign'
title: 'Create one-time audit for user groups'
type: 'POST'

layout: null
---

This method allows to create one-time audit for list of user groups.

### Request
* The headers must include a **valid api key**.
* **`templateId`** is id of audit template, **required**.
* **`auditObjectIds`** is array of audit object ids, **required if auditObjectGroupIds is not present**.
* **`auditObjectGroupIds`** is array of audit object group ids, **required if auditObjectIds is not present**.
* **`name`** is audit name, **required**.
* **`auditorHint`** is auditor hint visible during audit, **max length is 800 charachters**.
* **`useRandomAuditor`** is a flag where to use random auditor from group or use evenly distributed auditor from groups.
* **`assigneesGroupsIds`** is array of user group ids, which users audit is assigned to.
* **`startDate`** is audit start date UTC, optional.
* **`endDate`** is audit due date UTC, **required**.

```X-API-KEY:  abcdef12345```
```{
  "templateId": "string",
  "auditObjectIds": [
    "string"
  ],
  "auditObjectGroupIds": [
    "string"
  ],
  "name": "string",
  "auditorHint" : "string",
  "useRandomAuditor": true,
  "assigneesGroupsIds": [
    "string"
  ],
  "startDate": "2021-11-30T13:30:57.068Z",
  "endDate": "2021-12-30T13:30:57.068Z"
}```

### Response

**If succeeds**, returns an id of created schedule.

```Status: 200 OK```

```{
  "id": "string"
}```

For errors responses, see the [response status codes documentation](#/response-status-codes).
