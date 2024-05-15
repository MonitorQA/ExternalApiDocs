---
category: 2. Audits
url_path: '/audit'
title: 'Create one-time audit'
type: 'POST'
order: 1
layout: null
---

This method allows to create one-time audit for single user and single audit object 

### Request
* The headers must include a **valid api key**.
* **`startDate`** is audit start date UTC, optional.
* **`endDate`** is audit due date UTC, **required**.
* **`name`** is audit name, **required**.
* **`auditorHint`** is auditor hint visible during audit, **max length is 800 charachters**.
* **`templateId`** is id of audit template, **required**.
* **`auditObjectId`** is id of audit object, **required**.
* **`assigneeId`** is id of user, whom audit is assigned to.

```X-API-KEY:  abcdef12345```
```{
  "startDate": datetime,
  "endDate": datetime,
  "name": string,
  "auditorHint": string,
  "templateId": string,
  "auditObjectId": string,
  "assigneeId": string
}```

### Response

**If succeeds**, returns an id of created audit.

```Status: 200 OK```

```{
  "id": "string"
}```

For errors responses, see the [response status codes documentation](#/response-status-codes).
