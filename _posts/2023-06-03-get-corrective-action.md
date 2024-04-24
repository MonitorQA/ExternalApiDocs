---
category: 9. Corrective Actions
url_path: '/corrective-actions/{id}'
title: 'Get corrective action details'
type: 'GET'
order: 4
layout: null
---

This method allows to get details of corrective action.

### Request

* **`{id}`** is the id of corrective action, **required**.
* The headers must include a **valid api key**.


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

**If succeeds**, returns corrective action details.

```Status: 200 OK```

```{
   "answer": {
      "name": string,
      "points": number,
      "text": string,
      "number": number,
      "isFailed": boolean
   },
   "approvedAtUtc": date,
   "approvedBy": {
        "id": string, 
        "name": string
      },
   "assignedUsers": [
      {
         "id": string,
         "name": string
      }
   ],
   "audit": {
      "id": string,
      "name": string,
      "ianaTimeZone": string
   },
   "auditItemId": string,
   "auditObject": {
      "id": string,
      "name": string
   },
   "createdAtUtc": "2022-10-31T11:05:37.6888585",
   "createdBy": {
      "id": string,
      "name": string
   },
   "description": string,
   "dueDateUtc": "2022-11-01T06:59:59",
   "expiredAtUtc": date,
   "expiredBy": {
      "id": string,
      "name": string
   },
   "id": string,
   "information": {
      "text": string,
      "photosIds": [
         string
      ],
      "files": [
         {
            "id": string,
            "name": string,
            "contentType": string,
            "updatedAt": "2023-07-03T11:31:01.8187649Z"
         }
      ]
   },
   "name": string,
   "number": string,
   "priority": 0,
   "question": string,
   "status": 3,
   "tags": [
      {
         "id": string,
         "name": string
      }
   ],
   "files": [
      {
         "id": string,
         "name": string,
         "contentType": string,
         "updatedAt": "2022-10-31T11:05:37.6887695Z"
      }
   ]
}```


For errors responses, see the [response status codes documentation](#/response-status-codes).
