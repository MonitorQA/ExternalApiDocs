---
category: 3. Schedules
url_path: '/schedules/weekly'
title: '[SOON] Create weekly schedule'
type: 'POST'
order: 15
layout: null
---

This method allows to create weekly schedule for list of users. It will create new audits each week for selected days of week.

### Request
* The headers must include a **valid api key**.
* **`templateId`** is id of audit template, **required**.
* **`auditObjectIds`** is array of audit object ids, **required if auditObjectGroupIds is not present**.
* **`auditObjectGroupIds`** is array of audit object group ids, **required if auditObjectIds is not present**.
* **`name`** is audit name, **required**.
* **`auditorHint`** is auditor hint visible during audit, **max length is 800 charachters**.
* **`assigneesIds`** is array of user ids, whom audit is assigned to.
* **`daysOfWeek`** is array of days of week, **required**, **value: 0 - Sun, 1 - Mon, 2 - Tue, 3 - Wed, 4 - Thru, 5 - Fri, 6 - Sat**.


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
  "daysOfWeek": [3,6]
}```

### Response

**If succeeds**, returns an id of created schedule.

```Status: 200 OK```

```{
  "id": "string"
}```

For errors responses, see the [response status codes documentation](#/response-status-codes).