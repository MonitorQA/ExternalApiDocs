---
category: 10. Audit Object Attributes
url_path: '/audit/objects/attributes/{id}'
title: 'Update Audit Object Attribute'
type: 'PUT'
order: 4
layout: null
---

This method allows to update audit object attribute. First option with isDefault: true will be save as default value. Existing options should have "id" property. Options without "id" will be created. Options not listed in request will be deleted and audit object attribute assignments for these options will be deleted.
Options array should contain at least one option.

### Request

* **`{id}`** is the id of audit object attribute, **required**.
* The headers must include a **valid api key**.

```X-API-KEY:  abcdef12345```

* The body must contain audit object attribute

```{
   "options": [
      { // update option
         "isDefault": boolean
         "name": string, required
         "id": string         
      },
      { // create new option
         "isDefault": boolean
         "name": string, required
      }
   ],
   "name": string, required
}```

### Response

**If succeeds**, returns an empty response

```Status: 200 OK```

For errors responses, see the [response status codes documentation](#/response-status-codes).
