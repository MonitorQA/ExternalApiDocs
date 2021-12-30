---
category: Audit Templates
url_path: '/audit/templates'
title: 'Get audit templates list'
type: 'GET'

layout: null
---

This method allows to get audit templates list with id and name pairs.

### Request

* The headers must include a **valid api key**.

```X-API-KEY:  abcdef12345```

### Response

**If succeeds**, returns a list of audit templates id and name pairs.

```Status: 200 OK```

```[
  {
    "id": "string",
    "name": "string"
  }
]```

For errors responses, see the [response status codes documentation](#/response-status-codes).
