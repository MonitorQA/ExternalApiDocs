---
category: Audit Object Attributes
url_path: '/audit/objects/attributes'
title: 'Create Audit Object Attribute'
type: 'POST'

layout: null
---

This method allows to create audit object attribute. First option with isDefault: true will be save as default value.

### Request

* The headers must include a **valid api key**.

```X-API-KEY:  abcdef12345```

* The body must contain audit object attribute

```{
   "options": [
      {
         "isDefault": boolean,
         "name": string, required
      }
   ],
   "name": string, required
}```

### Response

**If succeeds**, returns an id of created attribute

```Status: 200 OK```

```{
   "id": string
}```

For errors responses, see the [response status codes documentation](#/response-status-codes).
