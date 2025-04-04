---
category: 7. Users
url_path: '/users'
title: 'Delete users'
type: 'DELETE'
order: 26
layout: null
---

This method allows to delete company users

### Request

* The headers must include a **valid api key**.
* The body must include array of users ids.

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
