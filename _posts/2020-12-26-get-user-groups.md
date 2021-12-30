---
category: User Groups
url_path: '/user-groups'
title: 'Get list of user groups'
type: 'GET'

layout: null
---

This method allows to get list of company user groups

### Request

* The headers must include a **valid api key**.

### Response

Returns a collection of company user groups.

```Status: 200 OK```
```[
  {
    "id": "string",
    "name": "string"
  }
]```

For errors responses, see the [response status codes documentation](#/response-status-codes).
