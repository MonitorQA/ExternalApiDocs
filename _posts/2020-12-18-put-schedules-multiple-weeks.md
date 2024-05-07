---
category: 3. Schedules
url_path: '/schedules/multiple-weeks'
title: '[SOON] Update multiple weeks schedule'
type: 'PUT'
order: 20
layout: null
---

This method allows to update multiple weeks schedule for list of users.

### Request
* The headers must include a **valid api key**.
* **`auditObjectIds`** is array of audit object ids, **required if auditObjectGroupIds is not present**.
* **`auditObjectGroupIds`** is array of audit object group ids, **required if auditObjectIds is not present**.
* **`name`** is audit name, **required**.
* **`auditorHint`** is auditor hint visible during audit, **max length is 800 charachters**.
* **`assigneesIds`** is array of user ids, whom audit is assigned to.
* **`repeatEvery`** is repeat value - how often create audit in weeks. 
* **`startDay`** is audit start month day, **required**. **values: 0 - Sun, 1 - Mon, 2 - Tue, 3 - Wed, 4 - Thru, 5 - Fri, 6 - Sat**.
* **`duration`** is audit duration in days, **required**. **value in range from 1 to *repeatEvery*\*7**


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
  "repeatEvery": 2,
  "startDay": 1,
  "duration": 14
}```

### Response

**If succeeds**, returns empty response.

```Status: 200 OK```

For errors responses, see the [response status codes documentation](#/response-status-codes).
