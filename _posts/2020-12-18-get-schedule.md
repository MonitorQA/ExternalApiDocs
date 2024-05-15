---
category: 3. Schedules
url_path: '/schedules/{scheduleId}'
title: 'Get schedule details'
type: 'GET'
order: 2
layout: null
---

This method allows to get schedule details.

### Request
* The headers must include a **valid api key**.

```X-API-KEY:  abcdef12345```

### Response

**If succeeds**, returns details of schedule.

* **`id`** is schedule id.
* **`name`** is schedule name.
* **`active`** is schedule status - inactive schedule doesn't generate audits.
* **`auditorHint`** is auditor hint visible during audit.
* **`template`** is information about template.
* **`assignees`** is information about users assigned to this schedule.
* **`auditObjects`** is information about audit objects assigned to this schedule.
* **`auditObjectGroups`** is information about audit object groups assigned to this schedule.
* **`repeatPattern`** is schedule repeat pattern.
* **`repeat`** is repeat options. Options vary depending on **`repeatPattern`** value.

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

**Example**

```Status: 200 OK```

```{
   "id": string,
   "name": string,
   "active": boolean,
   "auditorHint": string,
   "template": {
      "id": string,
      "name": string
   },
   "assignees": [
      {
         "id": string,
         "name": string
      }
   ],
   "auditObjects": [
      {
         "id": string,
         "name": string
      }
   ],
   "auditObjectGroups": [
      {
         "id": string,
         "name": string
      }
   ],
   "repeatPattern": 3, //Monthly audit
   "repeat": {
      "startDay": number,
      "duration": number,
      "repeatEvery": number
   }
}```

For errors responses, see the [response status codes documentation](#/response-status-codes).
