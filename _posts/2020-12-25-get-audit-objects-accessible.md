---
category: Audit Objects
url_path: '/audit/objects/accessible/{userId}'
title: 'Get list of audit objects accessible by user'
type: 'GET'

layout: null
---

This method allows to retrieve list of audit objects accessible by company user.

### Request

* **`{userId}`** is the id of user to check access to audit objects.
* The headers must include a **valid api key**.

### Response

Returns a collection of audit objects accessble by user.

```Status: 200 OK```
```[
  {
    "id": "string",
    "name": "string"
  }
]```

For errors responses, see the [response status codes documentation](#/response-status-codes).
