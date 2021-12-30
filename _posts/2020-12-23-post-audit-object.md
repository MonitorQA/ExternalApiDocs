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

**If succeeds**, returns an id of created audit object.

```Status: 200 OK```
```{
    "id": "string"   
}```

For errors responses, see the [response status codes documentation](#/response-status-codes).
