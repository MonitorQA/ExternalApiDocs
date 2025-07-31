---
category: 2. Audits
url_path: '/audit/{auditId}'
title: 'Get details of audit'
type: 'GET'
order: 7
layout: null
---

This method allows you to retrieve detailed information about a specific audit, including its status, assignees, completion details, and scoring information.

### Request Headers

| Header | Type | Required | Description |
|--------|------|----------|-------------|
| `X-API-KEY` | string | Yes | Your API authentication key |

### Path Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `auditId` | string | Yes | Unique identifier of the audit |

### Example Request

```http
GET /audit/123e4567-e89b-12d3-a456-426614174000
Host: api-external.monitorqa.com
X-API-KEY: abcdef12345
```

## Response

**Success Response**

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "id": "string",
  "auditorHint": "string",
  "companyId": "string",
  "number": "string",
  "auditObject": {
    "id": "string",
    "name": "string",
    "notes": "string"
  },
  "startedBy": {
    "id": "string",
    "name": "string"
  },
  "templateId": "string",
  "template": {
    "id": "string",
    "name": "string"
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
  "isExpired": false,
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
