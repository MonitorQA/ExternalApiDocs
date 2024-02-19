---
category: Audits
url_path: '/audit/pending'
title: 'Get list of pending audits'
type: 'GET'

layout: null
---

This method allows to get list of pending audits.

### Request
* The headers must include a **valid api key**.

```X-API-KEY:  abcdef12345```

### Optional Query String Parameters
* **`inProgress`** - filter by in progress state.
* **`templateId`** - filter by audit template id.
* **`auditObjectId`** - filter by audit object id.
* **`auditObjectGroupId`** - filter by audit object group id.
* **`assignedTo`** - filter by assigned to user id.
* **`assignedToGroup`** - filter by assigned to user group id.
* **`fromDate`** - filter by audit due date UTC.
* **`toDate`** - filter by audit due date UTC.
* **`pageNumber`** - current page number, starts from 1.
* **`pageSize`** - current page size.
* **`orderBy`** - field name to sort audits by (default value is 'name').
* **`orderByDirection`** - audits sorting direction.

Accepted values for **`orderBy`**:
* **`name`** - sort by audit name
* **`auditObjectName`** - sort by audit object name
* **`endDate`** - sort by audit end date
* **`assignedTo`** - sort by assigned user name

Accepted values for **`orderByDirection`**:
* **`asc`** - ascending
* **`desc`** - descending

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
      "endDate": "2021-12-30T13:46:13.413Z",
      "number": "string",
      "startDate": "2021-12-30T13:46:13.413Z",
      "template": {
        "id": "string",
        "name": "string"
      },
      "isReopened": true,
      "isStarted": true,
      "completedActionsCount": 0,
      "pendingActionsCount": 0
    }
  ],
  "meta": {
    "pageNumber": 0,
    "pageSize": 0,
    "totalCount": 0
  }
}```

For errors responses, see the [response status codes documentation](#/response-status-codes).
