---
category: 5. Audit Objects
url_path: '/audit/objects/{id}'
title: 'Update an audit object'
type: 'PUT'
order: 20
layout: null
---

This method allows to update existing audit object.

### Request

* **`{id}`** is the id of audit object, **required**.
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

**If succeeds**, returns an empty response.

```Status: 200 OK```

For errors responses, see the [response status codes documentation](#/response-status-codes).
