---
category: Audit Objects
url_path: '/audit/objects'
title: 'Delete audit objects'
type: 'DELETE'

layout: null
---

This method allows to delete a number of audit objects.

### Request

* The headers must include a **valid api key**.
* The body must include array of audit object ids.

```X-API-KEY:  abcdef12345```

```{
  "ids": [
    "string"
  ]
}```

### Response

**If succeeds**, returns an empty response.

```Status: 200 OK```

For errors responses, see the [response status codes documentation](#/response-status-codes).
