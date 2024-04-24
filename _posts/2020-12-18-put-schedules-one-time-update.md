---
category: 3. Schedules
url_path: '/schedules/one-time/{scheduleId}'
title: 'Update one-time audit schedule'
type: 'PUT'
order: 14
layout: null
---

This method allows to update one-time audit schedule.

### Request
* The headers must include a **valid api key**.
* **`name`** is audit name, **required**.
* **`startDate`** is audit start date UTC, optional.
* **`endDate`** is audit due date UTC, **required**.

```X-API-KEY:  abcdef12345```
```{
  "name": "string",
  "startDate": "2021-11-30T13:30:57.068Z",
  "endDate": "2021-12-30T13:30:57.068Z"
}```

### Response

**If succeeds**, returns an empty response.

```Status: 200 OK```

For errors responses, see the [response status codes documentation](#/response-status-codes).
