---
category: Schedules
url_path: '/schedules/ad-hoc'
title: 'Create ad-hoc audit for user'
type: 'POST'

layout: null
---

This method allows to create ad-hoc audit for specified user.

### Request
* The headers must include a **valid api key**.
* **`date`** is audit due date, **required**.
* **`name`** is audit name, **required**.
* **`templateId`** is id of audit template, **required**.
* **`auditObjectId`** is id of audit object, **required**.
* **`userId`** is id of user, whom audit is assigned to.

```X-API-KEY:  abcdef12345```
```{
  "name": "string",
  "date": "2021-12-30T13:40:46.382Z",
  "templateId": "string",
  "auditObjectId": "string",
  "userId": "string"
}```

### Response

**If succeeds**, returns an id of created audit.

```Status: 200 OK```

```{
  "id": "string"
}```

For errors responses, see the [response status codes documentation](#/response-status-codes).
