---
category: 2. Audits
url_path: '/audit/reopen/{id}'
title: 'Reopen Audit'
type: 'POST'
order: 20
layout: null
---

This method allows to reopen completed audit.

### Request

* **`{id}`** is the id of completed audit, **required**.
* The headers must include a **valid api key**.

* The body must include start and end dates. Assignees list is optional. Audit assignees will not changed if assignees list is null. Empty list will remove all assignees from audit.

* **`startDate`** is audit local start date, **required**.
* **`endDate`** is audit local due date, **required**.
* **`assigneesIds`** is array of user ids, whom audit is assigned to.

```X-API-KEY:  abcdef12345```

```{
  "assigneesIds": [
    "string"
  ],
  "startDate": "2021-11-30T13:30:57.068Z",
  "endDate": "2021-12-30T13:30:57.068Z"
}```

### Response

**If succeeds**, returns an empty response.

```Status: 200 OK```

For errors responses, see the [response status codes documentation](#/response-status-codes).
