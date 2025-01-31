---
category: 2. Audits
url_path: '/audit/expire'
title: 'Expire Audit'
type: 'POST'
order: 24
layout: null
---

This method allows to expire not completed audits.

### Request

* The headers must include a **valid api key**.
* The body must include array of audits ids.

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
