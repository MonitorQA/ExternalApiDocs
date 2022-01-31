---
category: Audit Objects
url_path: '/audit/objects/{id}'
title: 'Update an audit object'
type: 'PUT'

layout: null
---

This method allows to update existing audit object.

### Request

* **`{id}`** is the id of audit object, **required**.
* The headers must include a **valid api key**.

* The body must include audit object data.
* **`name`** is audit object name, **required**.
* **`geoAddress`** is audit object address information.
* **`participanUserIds`** is array of user ids.
* **`participantUserGroupIds`** is array of user group ids.

```X-API-KEY:  abcdef12345```

```{
  "name": "string",
  "geoAddress": {
    "lat": "string",
    "lng": "string",
    "name": "string",
    "address": "string"
  },
  "participantUserIds": [
    "string"
  ],
  "participantUserGroupIds": [
    "string"
  ]
}```

### Response

**If succeeds**, returns an empty response.

```Status: 200 OK```

For errors responses, see the [response status codes documentation](#/response-status-codes).
