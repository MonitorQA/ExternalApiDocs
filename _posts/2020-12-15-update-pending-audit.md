---
category: 2. Audits
url_path: '/audit/pending/{auditId}'
title: 'Update pending audit'
type: 'PUT'
order: 7
layout: null
---

This method allows to update pending audit.

### Request

* **`{auditId}`** is the id of audit, **required**.
* The headers must include a **valid api key**.

* The body must include audit data.
* **`name`** is audit name, **required**.
* **`startDate`** is audit start date UTC, **required**.
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

Returns error **`409  audit/action-not-allowed`** when trying to update completed or expired audit or audit is not one-time audit.

For errors responses, see the [response status codes documentation](#/response-status-codes).
