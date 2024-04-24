---
category: 10. Audit Object Attributes
url_path: '/audit/objects/attributes/all'
title: 'Get Audit Object Attributes List'
type: 'GET'
order: 1
layout: null
---

This method allows to get list of audit object attributes.

### Request

* The headers must include a **valid api key**.

```X-API-KEY:  abcdef12345```

### Response

**If succeeds**, returns a list of audit object attributes

```Status: 200 OK```

```[
   {
      "options": [
         {
            "isDefault": boolean,
            "name": string,
            "id": string
         }
      ],
      "name": string,
      "id": string
   }
]```

For errors responses, see the [response status codes documentation](#/response-status-codes).
