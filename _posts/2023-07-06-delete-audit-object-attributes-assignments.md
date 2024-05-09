---
category: 5. Audit Objects
url_path: '/audit/objects/{id}/attributes'
title: 'Delete Attributes Assignments from Audit Object'
type: 'DELETE'
order: 2
layout: null
---

This method allows to delete attributes assignments from audit object. Invalid attribute ids and options ids are ignored.

### Request

* **`{id}`** is the id of audit object, **required**.
* The headers must include a **valid api key**.

```X-API-KEY:  abcdef12345```

```{
 "attributes": [
     {
        "attributeId": string,
        "optionId": string
     }
 ]
}```

### Response

**If succeeds**, returns an empty response.

```Status: 200 OK```


For errors responses, see the [response status codes documentation](#/response-status-codes).
