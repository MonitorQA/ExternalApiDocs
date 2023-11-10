---
category: Audit Objects
url_path: '/audit/objects'
title: 'Create a new audit object'
type: 'POST'

layout: null
---

This method allows to create new audit object.

### Request

* The headers must include a **valid api key**.
* The body must include audit object data.
* **`name`** is audit object name, **required**.
* **`notes`** is audit object notes visible for auditor during audit, **max length is 800 chracters**.
* **`geoAddress`** is audit object address information. All fields of geoAddress are **required** when geoAdress is not null.


```X-API-KEY:  abcdef12345```

```{
  "name": "string",
  "notes": "string",
  "geoAddress": {
    "lat": "string",
    "lng": "string",
    "name": "string",
    "address": "string"
  }
}```

### Response

**If succeeds**, returns an id of created audit object.

```Status: 200 OK```
```{
    "id": "string"   
}```

For errors responses, see the [response status codes documentation](#/response-status-codes).
