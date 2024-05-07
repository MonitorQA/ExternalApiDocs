---
category: 3. Schedules
url_path: '/schedules/daily/{scheduleId}'
title: '[SOON] Update daily schedule'
type: 'PUT'
order: 18
layout: null
---

This method allows to update daily schedule.

### Request
* The headers must include a **valid api key**.
* **`auditObjectIds`** is array of audit object ids, **required if auditObjectGroupIds is not present**.
* **`auditObjectGroupIds`** is array of audit object group ids, **required if auditObjectIds is not present**.
* **`name`** is audit name, **required**.
* **`auditorHint`** is auditor hint visible during audit, **max length is 800 charachters**.
* **`assigneesIds`** is array of user ids, whom audit is assigned to.
* **`repeatEvery`** is repeat value - how often to create audits in days. **required**, **value in range 1 to 10**.

```X-API-KEY:  abcdef12345```
```{
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
  "repeatEvery": 3
}```

### Response

**If succeeds**, returns an empty response..

```Status: 200 OK```

For errors responses, see the [response status codes documentation](#/response-status-codes).
