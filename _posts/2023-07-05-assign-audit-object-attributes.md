---
category: 5. Audit Objects
url_path: '/audit/objects/{id}/attributes'
title: 'Assign Attributes to Audit Object'
type: 'POST'
order: 1
layout: null
---

This method allows to assign attributes to audit object. Is is not possible to assign same option twice. Option should be available for specified attribute or it won't be assigned.

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
