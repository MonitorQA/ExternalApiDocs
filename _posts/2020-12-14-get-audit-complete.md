---
category: Audits
url_path: '/audit/complete'
title: 'Get list of complete audits'
type: 'GET'

layout: null
---

This method allows to get list of complete audits.

### Request
* The headers must include a **valid api key**.

```X-API-KEY:  abcdef12345```

### Optional Query String Parameters
* **`scoreMin`** - filter by minimum score.
* **`scoreMax`** - filter by maximum score.
* **`completedBy`** - filter by user group id which user completed audit.
* **`completedByGroup`** - filter by completed by user id.
* **`templateId`** - filter by audit template id.
* **`auditObjectId`** - filter by audit object id.
* **`auditObjectGroupId`** - filter by audit object group id.
* **`assignedTo`** - filter by assigned to user id.
* **`assignedToGroup`** - filter by assigned to user group id.
* **`fromDate`** - filter by audit completion date UTC.
* **`toDate`** - filter by audit completion date UTC.
* **`pageNumber`** - current page number, starts from 1.
* **`pageSize`** - current page size.

### Response

**If succeeds**, returns a list of audit details.

```Status: 200 OK```

```{
  "data": [
    {
      "id": "string",
      "assignees": [
        {
          "id": "string",
          "name": "string"
        }
      ],
      "auditObject": {
        "id": "string",
        "name": "string"
      },
      "auditSchedule": {
        "id": "string",
        "name": "string",
        "repeatPattern": 0,
        "templateId": "string"
      },
      "endDate": "2021-12-30T13:57:38.999Z",
      "number": "string",
      "startDate": "2021-12-30T13:57:38.999Z",
      "template": {
        "id": "string",
        "name": "string"
      },
      "completeDate": "2021-12-30T13:57:38.999Z",
      "completedBy": {
        "id": "string",
        "name": "string"
      },
      "score": 0,
      "scoreLabel": "string"
    }
  ],
  "meta": {
    "pageNumber": 0,
    "pageSize": 0,
    "totalCount": 0
  }
}```

For errors responses, see the [response status codes documentation](#/response-status-codes).
