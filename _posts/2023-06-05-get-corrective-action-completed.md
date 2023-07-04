---
category: Corrective Actions
url_path: '/corrective-actions/completed'
title: 'Get completed corrective actions list'
type: 'GET'

layout: null
---

This method allows to get list of completed corrective actions.


### Request
* The headers must include a **valid api key**.

```X-API-KEY:  abcdef12345```

### Optional Query String Parameters
* **`auditId`** - filter by audit id.
* **`templateId`** - filter by audit template id.
* **`auditObjectId`** - filter by audit object id.
* **`assignedToId`** - filter by assigned to user id.
* **`approvedById`** - filter by approved by user id.
* **`assignedToGroupId`** - filter by assigned to user group id.
* **`fromDate`** - filter by corrective action due date UTC.
* **`toDate`** - filter by corrective action due date UTC.
* **`pageNumber`** - current page number, starts from 1.
* **`pageSize`** - current page size.

### Response

Possible corrective action statuses:

```   0 - Open,
  1 - Approved,
  2 - Rejected,
  3 - Submitted,
  4 - Expired```

Possible corrective action priorities:

```   0 - Low,
  1 - Medium,
  2 - High```
  

**If succeeds**, returns a list of completed corrective actions.


```Status: 200 OK```

```{
   "data": [
        {
         "id": string,
         "name": string,
         "number": string,
         "assignedUsers": [
            {
               "id": string,
               "name": string
            }
         ],
         "audit": {
            "id": string,
            "name": string,
            "ianaTimeZone": string,
            "number": string
         },
         "createdBy": {
            "id": string,
            "name": string
         },
         "auditObject": {
            "id": string,
            "name": string
         },
         "status": 1,
         "priority": 0,
         "createdAtUtc": date,
         "dueDateUtc": date,
         "approvedBy": {
            "id": string,
            "name": string
         },
         "approvedAtUtc": date
      },
      ...
   ],
   "meta": {
      "pageNumber": number,
      "pageSize": number,
      "totalCount": number
   }
}```


For errors responses, see the [response status codes documentation](#/response-status-codes).
