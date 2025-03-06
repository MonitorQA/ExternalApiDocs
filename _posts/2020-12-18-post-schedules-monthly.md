---
category: 3. Schedules
url_path: '/schedules/monthly'
title: 'Create monthly schedule'
type: 'POST'
order: 17
layout: null
---

This method allows to create monthly schedule for list of users. It will create new audits each *repeatEvery* month at selected *startDay*.

### Request
* The headers must include a **valid api key**.
* **`templateId`** is id of audit template, **required**.
* **`auditObjectIds`** is array of audit object ids, **required if auditObjectGroupIds is not present**.
* **`auditObjectGroupIds`** is array of audit object group ids, **required if auditObjectIds is not present**.
* **`name`** is schedule name, **required**.
* **`auditorHint`** is auditor hint visible during audit, **max length is 2000 charachters**.
* **`assigneesIds`** is array of user ids, whom audit is assigned to.
* **`repeatEvery`** is repeat value - how often create audit in months. 
* **`startDay`** is audit start month day, **required**. **value in range from 1 to 31**. If there are no date with this number, last day of month will be used.
* **`duration`** is audit duration in days, **required**. **value in range from 1 to *repeatEvery*\*31**
* **`active`** is schedule status, **optional**, **true** by default.
* **`startFromDate`** local date when schedule should be started,**optional**.
* **`stopByDate`** local date after which schedule should be stopped,**optional**.

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
  "auditorHint": "string",
  "assigneesIds": [
    "string"
  ],
  "repeatEvery": 1,
  "startDay": 2,
  "duration": 18
}```

### Response

**If succeeds**, returns an id of created schedule.

```Status: 200 OK```

```{
  "id": "string"
}```

For errors responses, see the [response status codes documentation](#/response-status-codes).
