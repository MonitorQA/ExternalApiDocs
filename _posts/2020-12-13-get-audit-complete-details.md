---
category: 2. Audits
url_path: '/audit/complete/{auditId}'
title: 'Get details of complete audit'
type: 'GET'
order: 2
layout: null
---

Retrieve comprehensive details of a completed audit, including audit metadata, assignees, completion status, and reporting information.

### Request Headers

| Header | Type | Required | Description |
|--------|------|----------|-------------|
| `X-API-KEY` | string | Yes | API authentication key |

### Path Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `auditId` | string | Yes | Unique identifier of the completed audit |

### Example Request

```http
GET /audit/complete/{auditId}
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
  "companyId": "b2c3d4e5-f6a7-890b-cdef-012345678901",
  "number": "AUD-2023-0475",
  "auditorHint": "Pay special attention to cold storage temperature logs and cleaning schedules",
  "auditObject": {
    "id": "c3d4e5f6-a7b8-901c-defa-123456789012",
    "name": "Warehouse Cold Storage Unit B",
    "notes": "Temperature-controlled environment for perishable goods"
  },
  "startedBy": {
    "id": "d4e5f6a7-b8c9-012d-efab-234567890123",
    "name": "Michael Johnson"
  },
  "templateId": "e5f6a7b8-c9d0-123e-fabc-345678901234",
  "template": {
    "id": "e5f6a7b8-c9d0-123e-fabc-345678901234",
    "name": "Cold Storage Compliance Audit"
  },
  "assignees": [
    {
      "id": "f6a7b8c9-d0e1-234f-abcd-456789012345",
      "name": "Rachel Kim"
    },
    {
      "id": "a7b8c9d0-e1f2-345a-bcde-567890123456",
      "name": "Carlos Rodriguez"
    }
  ],
  "isStarted": true,
  "isFailed": false,
  "startedAt": "2023-10-25T07:30:00.000Z",
  "isCompleted": true,
  "completeDate": "2023-10-25T11:45:33.875Z",
  "isExpired": false,
  "isReopened": false,
  "completedBy": {
    "id": "f6a7b8c9-d0e1-234f-abcd-456789012345",
    "name": "Rachel Kim"
  },
  "startDate": "2023-10-25T07:00:00.000Z",
  "endDate": "2023-10-25T15:00:00.000Z",
  "score": 91,
  "scoreLabel": "Excellent",
  "scoreColor": "#198754",
  "completionTime": 255,
  "reportUrl": "https://api-external.monitorqa.com/reports/audit/a1b2c3d4-e5f6-789a-bcde-f01234567890",
   "auditeeSignature": {
      "photoId": "d1b4b954-3e9f-4d93-bdeb-a4112f1ed26e",
      "createdBy": {
         "id": "00000000-0000-0000-0000-000000000000",
         "name": "Auditee name"
      }
   },
   "auditorSignature": {
      "photoId": "c54e4562-3ce2-4957-b1f0-2dd96405de29",
      "createdBy": {
         "id": "3c71b2a5-4c01-4bb0-9f08-785a2d8f7128",
         "name": "Rachel Kim"
      }
   }
}
```

For errors responses, see the [response status codes documentation](#/response-status-codes).
