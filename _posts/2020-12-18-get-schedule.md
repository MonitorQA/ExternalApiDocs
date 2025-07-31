---
category: 3. Schedules
url_path: '/schedules/{scheduleId}'
title: 'Get schedule details'
type: 'GET'
order: 2
layout: null
---

This method allows you to retrieve detailed information about a specific schedule, including its configuration, repeat patterns, and assigned objects.

### Request Headers

| Header | Type | Required | Description |
|--------|------|----------|-------------|
| `X-API-KEY` | string | Yes | Your API authentication key |

### Path Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `scheduleId` | string | Yes | Unique identifier of the schedule |

### Example Request

```http
GET /schedules/{scheduleId}
Host: api-external.monitorqa.com
X-API-KEY: abcdef12345
```

### Response

**If succeeds**, returns details of schedule.

* **`id`** is schedule id.
* **`name`** is schedule name.
* **`active`** is schedule status - inactive schedule doesn't generate audits.
* **`stopByDate`** is schedule last active date. Schedule will be deactivated after this date and will not generate new audits.
* **`startFromDate`** is schedule activation date. Schedule will be activated at this date and will generate new audits.
* **`auditorHint`** is auditor hint visible during audit.
* **`template`** is information about template.
* **`assignees`** is information about users assigned to this schedule.
* **`auditObjects`** is information about audit objects assigned to this schedule.
* **`auditObjectGroups`** is information about audit object groups assigned to this schedule.
* **`repeatPattern`** is schedule repeat pattern.
* **`repeat`** is repeat options. Options vary depending on **`repeatPattern`** value.

### Repeat Patterns

| Pattern | Description |
|---------|-------------|
| `0` | One-time audit - produces one audit with no repeat |
| `1` | Daily audit - repeats daily with configurable interval |
| `2` | Multiple weeks audit - repeats per week with configurable interval and start day |
| `3` | Monthly audit - repeats per month with configurable interval and start day |
| `4` | Weekly audit - repeats on specific days of week |

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
   "stopByDate": datetime,
   "startFromDate": datetime,
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
