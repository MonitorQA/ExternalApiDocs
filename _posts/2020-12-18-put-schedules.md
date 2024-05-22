---
category: 3. Schedules
url_path: '/schedules/{scheduleId}'
title: 'Update schedule'
type: 'PUT'
order: 18
layout: null
---

This method allows to update schedule.

### Request
* The headers must include a **valid api key**.
* **`auditObjectIds`** is array of audit object ids, **required if auditObjectGroupIds is not present**.
* **`auditObjectGroupIds`** is array of audit object group ids, **required if auditObjectIds is not present**.
* **`name`** is schedule name, **required**.
* **`auditorHint`** is auditor hint visible during audit, **max length is 800 charachters**.
* **`assigneesIds`** is array of user ids, whom audit is assigned to.
* **`repeatPattern`** is schedule repeat pattern. **required**, **values: 0 - One-time, 1 - Daily, 2 - Multiple Weeks, 3 - Monthly, 4 - Weekly**.
* **`repeat`** is repeat options. Options vary depending on **`repeatPattern`** value.
* **`active`** is schedule status, **optional**, **true** by default, **ignored for one-time audits**
* **`startFromDate`** local date when schedule should be started, **optional**, **ignored for one-time audits**.
* **`stopByDate`** local date after which schedule should be stopped, **optional**, **ignored for one-time audits**

**Repeat patterns**

* **`0`** - One-time audit. Schedule produces one audit with no repeat. Audit dates configured with repeat options.
* **`1`** - Daily audit. Schedule produces audits repeated daily. Repeat interval in days can be configured with repeat options.
* **`2`** - Multiple weeks audit. Schedule produces audits repeated per week. Repeat interval in weeks and audit start day of week can be configured with repeat options.
* **`3`** - Monthly audit. Schedule produces audits repeated per month. Repeat interval in months and audit start day of month can be configured with repeat options.
* **`4`** - Weekly audit. Schedule produces audits repeated per days of week. Days of week for audits can be configured with repeat options.

**Repeat options**

One-time audit repeat options:

```{
  "startDate": datetime,
  "endDate": datetime
}```

Daily audit repeat options:

```{
  "repeatEvery": number, //value in range 1..10
}```

Multiple weeks audit repeat options:

```{
  "repeatEvery": number, //value in range 1..10
  "startDay": DayOfWeek, //0 - Sun ... 6 - Sat
  "duration": number //value in range 1..repeatEvery*7
}```

Monthly audit repeat options:

```{
  "repeatEvery": number, //value in range 1..10
  "startDay": number, //value in range 1..31
  "duration": number  //value in range 1..repeatEvery*31
}```

Weekly audits repeat options:

```{
  "daysOfWeek": DayOfWeek[] //0 - Sun ... 6 - Sat
}```


### Example

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
  "repeatPattern": 1,
  "repeat": {
    "repeatEvery": 5
  }
}```

### Response

**If succeeds**, returns an empty response.

```Status: 200 OK```

For errors responses, see the [response status codes documentation](#/response-status-codes).
