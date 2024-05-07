---
category: 5. Audit Objects
url_path: '/audit/objects'
title: 'Get list of audit objects'
type: 'GET'
order: 17
layout: null
---

This method allows to retrieve list of all audit objects belong to company.

### Request

* The headers must include a **valid api key**.

### Response

Returns a collection of audit objects.

```Status: 200 OK```
```[
  {
    "id": "string",
    "name": "string"
  }
]```

For errors responses, see the [response status codes documentation](#/response-status-codes).
