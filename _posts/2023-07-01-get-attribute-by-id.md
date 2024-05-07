---
category: 10. Audit Object Attributes
url_path: '/audit/objects/attributes/{id}'
title: 'Get Audit Object Attribute Details'
type: 'GET'
order: 2
layout: null
---

This method allows to get details of audit object attribute.

### Request

* **`{id}`** is the id of audit object attribute, **required**.
* The headers must include a **valid api key**.

```X-API-KEY:  abcdef12345```

### Response

**If succeeds**, returns details of audit object attribute

```Status: 200 OK```

```{
      "options": [
         {
            "isDefault": boolean,
            "name": string,
            "id": string
         }
      ],
      "name": string,
      "id": string
   }```

For errors responses, see the [response status codes documentation](#/response-status-codes).
