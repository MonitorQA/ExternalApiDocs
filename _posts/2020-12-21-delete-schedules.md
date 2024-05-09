---
category: 3. Schedules
url_path: '/schedules'
title: 'Delete schedules'
type: 'DELETE'
order: 23
layout: null
---

This method allows to delete a number of schedules. **All not started audits for selected schedules will be deleted**

### Request

* The headers must include a **valid api key**.
* The body must include array of schedules ids.

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
