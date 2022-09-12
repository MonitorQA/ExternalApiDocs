---
category: Audit
url_path: '/audit/complete/{auditId}/report'
title: 'Get audit report'
type: 'GET'

layout: null
---

This method allows to get report of complete audit.

### Request
* **`{auditId}`** is id of complete audit, **required**.
* The headers must include a **valid api key**.

```X-API-KEY:  abcdef12345```

### Response

**If succeeds**, returns complete audit items report.

```Status: 200 OK```

```{
   "id": "1acad6ca-cab8-48a7-07f2-08da929c74ab",
   "items": [
      {
         "id": "4ff6fbf7-8e6d-46be-356c-08da929d03c7",
         "text": string,
         "note": string,
         "notApplicable": boolean,
         "isCritical": boolean,
         "isPassed": boolean?,
         "childrenIds": [],
         "actions": [
            {
               "id": string,
               "name": string,
               "number": string,
               "description": "dd",
               "assignees": [
                    {
                        "id": string,
                        "name": string
                    }
                ],
               "comments": [],
               "createdBy": {
                  "id": "3c71b2a5-4c00-4bb0-9f08-785a2d8f7128",
                  "name": string
               },
               "createdAt": "2022-09-12T03:10:30.1333781",
               "dueDate": "2022-09-27T23:59:59.9999999",
               "priority": 0,
               "status": 0,
               "photos": [],
               "tags": []
            }
         ],
         "photos": [],
         "itemsCount": null,
         "points": null,
         "signature": null,
         "failedInRowCount": 1,
         "itemType": 2,
         "data": {
            "name": null,
            "points": 0.0000,
            "text": null,
            "number": 4.0000,
            "isFailed": true
         }
      }
   ]
}```

**itemType** possible values:
  * Root = 0,
  * Section = 1,
  * Item = 2,
  * ConditionalItem = 3,
  * Condition = 4,

**actions.priority** possible values:
  * Low = 0,
  * Medium = 1,
  * High = 2

**actions.status** possible values:
  * Open = 0,
  * Approved = 1,
  * Rejected = 2, 
  * Submitted = 3,

For errors responses, see the [response status codes documentation](#/response-status-codes).
