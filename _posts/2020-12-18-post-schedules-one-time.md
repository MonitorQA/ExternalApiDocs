---
category: Schedules
url_path: '/schedules/one-time'
title: 'Create one-time audit for users'
type: 'POST'

layout: null
---

This method allows to create one-time audit for list of users.

### Request
* The headers must include a **valid api key**.
* **`templateId`** is id of audit template, **required**.
* **`auditObjectIds`** is array of audit object ids, **required if auditObjectGroupIds is not present**.
* **`auditObjectGroupIds`** is array of audit object group ids, **required if auditObjectIds is not present**.
* **`name`** is audit name, **required**.
* **`assigneesIds`** is array of user ids, whom audit is assigned to.
* **`date`** is audit due date UTC, **required**.

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
  "assigneesIds": [
    "string"
  ],
  "date": "2021-12-30T13:07:35.093Z"
}```

### Response

**If succeeds**, returns an id of created schedule.

```Status: 200 OK```

```{
  "id": "string"
}```

For errors responses, see the [response status codes documentation](#/response-status-codes).
