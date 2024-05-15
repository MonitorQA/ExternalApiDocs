---
category: 3. Schedules
url_path: '/schedules/{scheduleId}/status'
title: 'Set schedule status'
type: 'POST'
order: 21
layout: null
---

This method allows to set schedule status. All schedules are active when created.
**This method can't be used with one-time schedules.**

### Request
* The headers must include a **valid api key**.

* **`active`** is schedule status, **required**.
* **`stopByDate`** date after which schedule should be stopped,**optional**, **used when active:true**.
* **`startFromDate`** date when schedule should be started,**optional**, **used when active:false**.

**Disable schedule with optional activation date**

All schedules are active by default. Schedule can be deactivated by passing **`active: false`**. Optional activation date can be passed at **`startByDate`** property. Schedule will be activated at selected date and audits will be created.

```X-API-KEY:  abcdef12345```
```{
  "active": false,
  "startFromDate": datetime
}```

**Enable disabled schedule with optional deactivation date**

Deactivated schedule can be activated by passing **`active: true`**. Optional deactivation date can be passed at **`StopByDate`**. Schedule will be stopped next day after selected date.

```X-API-KEY:  abcdef12345```
```{
  "active": true,
  "stopByDate": datetime
}```

### Response

**If succeeds**, returns an empty response.

```Status: 200 OK```

For errors responses, see the [response status codes documentation](#/response-status-codes).
