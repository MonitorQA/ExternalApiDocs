---
category: 2. Audits
url_path: '/audit/{auditId}'
title: 'Get details of audit'
type: 'GET'
order: 3
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
  "id": "a1b2c3d4-e5f6-789a-bcde-f01234567890",
  "auditorHint": "Check all emergency exits are clear and properly marked",
  "companyId": "b2c3d4e5-f6a7-890b-cdef-012345678901",
  "number": "AUD-2023-0892",
  "auditObject": {
    "id": "c3d4e5f6-a7b8-901c-defa-123456789012",
    "name": "Corporate Headquarters - Floor 3",
    "notes": "High traffic area with multiple conference rooms"
  },
  "startedBy": {
    "id": "d4e5f6a7-b8c9-012d-efab-234567890123",
    "name": "Jennifer Thompson"
  },
  "templateId": "e5f6a7b8-c9d0-123e-fabc-345678901234",
  "template": {
    "id": "e5f6a7b8-c9d0-123e-fabc-345678901234",
    "name": "Fire Safety and Emergency Preparedness Audit"
  },
  "assignees": [
    {
      "id": "f6a7b8c9-d0e1-234f-abcd-456789012345",
      "name": "David Lee"
    },
    {
      "id": "a7b8c9d0-e1f2-345a-bcde-567890123456",
      "name": "Amanda Rodriguez"
    }
  ],
  "isStarted": true,
  "startedAt": "2023-11-15T09:30:00.000Z",
  "isCompleted": true,
  "completeDate": "2023-11-15T14:45:22.150Z",
  "isFailed": false,
  "isExpired": false,
  "isReopened": false,
  "completedBy": {
    "id": "f6a7b8c9-d0e1-234f-abcd-456789012345",
    "name": "David Lee"
  },
  "startDate": "2023-11-15T09:00:00.000Z",
  "endDate": "2023-11-15T17:00:00.000Z",
  "score": 87,
  "scoreLabel": "Good",
  "scoreColor": "#28a745",
  "completionTime": 315
}
```

For errors responses, see the [response status codes documentation](#/response-status-codes).
