---
category: Audit
url_path: '/audit/complete/{auditId}'
title: 'Get details of complete audit'
type: 'GET'

layout: null
---

This method allows to get details of complete audit.

### Request
* **`{auditId}`** is id of complete audit, **required**.
* The headers must include a **valid api key**.

```X-API-KEY:  abcdef12345```

### Response

**If succeeds**, returns complete audit details.

```Status: 200 OK```

```{
  "id": "string",
  "companyId": "string",
  "number": "string",
  "auditObject": {
    "id": "string",
    "name": "string"
  },
  "startedBy": {
    "id": "string",
    "name": "string"
  },
  "templateId": "string",
  "auditSchedule": {
    "id": "string",
    "name": "string",
    "repeatPattern": 0,
    "templateId": "string"
  },
  "assignees": [
    {
      "id": "string",
      "name": "string"
    }
  ],
  "isStarted": true,
  "startedAt": "2021-12-30T14:11:23.202Z",
  "isCompleted": true,
  "completeDate": "2021-12-30T14:11:23.202Z",
  "isReopened": true,
  "completedBy": {
    "id": "string",
    "name": "string"
  },
  "startDate": "2021-12-30T14:11:23.202Z",
  "endDate": "2021-12-30T14:11:23.202Z",
  "score": 0,
  "scoreLabel": "string",
  "scoreColor": "string",
  "completionTime": 0
}```

For errors responses, see the [response status codes documentation](#/response-status-codes).
