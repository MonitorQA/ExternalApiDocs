---
category: Audit Objects
url_path: '/audit/object/{id}'
title: 'Get an audit object details'
type: 'GET'

layout: null
---

This method allows to get audit object details.

### Request

* **`{id}`** is the id of audit object, **required**.
* The headers must include a **valid api key**.

### Response

Returns details of audit object.

```Status: 200 OK```
```{
  "id": "string",
  "name": "string",
  "notes": "string",
  "participantUserGroups": [
    {
      "id": "string",
      "name": "string"
    }
  ],
  "participantUsers": [
    {
      "id": "string",
      "name": "string"
    }
  ],
  "auditObjectGroupIds": [
    "string"
  ],
  "attributes": [
      {
         "attributeId": string,
         "attributeName": string,
         "optionId": string,
         "optionName": string
      }
  ],    
  "geoAddress": {
    "lat": "string",
    "lng": "string",
    "name": "string",
    "address": "string"
  }
}```

For errors responses, see the [response status codes documentation](#/response-status-codes).
