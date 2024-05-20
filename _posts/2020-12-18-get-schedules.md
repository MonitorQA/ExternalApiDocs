---
category: 3. Schedules
url_path: '/schedules'
title: 'Get schedules list'
type: 'GET'
order: 1
layout: null
---

This method allows to get list of active schedules.

### Request
* The headers must include a **valid api key**.

### Optional Query String Parameters
* **`auditObjectId`** - filter by audit object id.
* **`auditObjectGroupId`** - filter by audit object group id.
* **`pageNumber`** - current page number, starts from 1.
* **`pageSize`** - current page size.
* **`orderBy`** - field name to sort audits by \(default value is 'name'\).
* **`orderByDirection`** - audits sorting direction.

Accepted values for **`orderBy`**:
* **`name`** - sort by audit name
* **`auditObject`** - sort by audit object name

Accepted values for **`orderByDirection`**:
* **`asc`** - ascending
* **`desc`** - descending

### Example

```X-API-KEY:  abcdef12345```

### Response

**If succeeds**, returns a list of schedules.
See [schedule details](#/get-schedule) for details about **`repeatPattern`** and **`repeat`** options


```Status: 200 OK```

```{
  "data": [
     {
         "id": string,
         "name": string,
         "repeatPattern": 1,
         "active": boolean,
         "stopByDate": datetime,
         "startFromDate": datetime,
         "template": {
            "id": string,
            "name": string
         },
         "repeat": {
            "repeatEvery": 3
         },
         "auditObjects: [{
            "id": string,
            "name": string
         }],
         "auditObjectGroups": [{
            "id": string,
            "name": string
         }]
      }
  ],
  "meta": {
    "pageNumber": 0,
    "pageSize": 10,
    "totalCount": 1
  }
}```

For errors responses, see the [response status codes documentation](#/response-status-codes).
