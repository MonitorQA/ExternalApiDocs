---
category: 10. Audit Object Attributes
url_path: '/audit/objects/attributes'
title: 'Delete Audit Object Attribute'
type: 'DELETE'
order: 5
layout: null
---

This method allows to delete audit object attributes. It will also delete audit object attributes assignments.


### Request

* The headers must include a **valid api key**.
* The body must include array of audit object attributes ids.

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
