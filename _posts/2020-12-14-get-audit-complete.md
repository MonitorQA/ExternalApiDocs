---
category: Audits
categoryOrder: 2
url_path: '/audit/complete'
title: 'Get list of complete audits'
type: 'GET'
order: 2
layout: null
---

Retrieve a paginated list of completed audits with advanced filtering and sorting options.

### Request Headers

| Header | Type | Required | Description |
|--------|------|----------|-------------|
| `X-API-KEY` | string | Yes | API authentication key |

### Query Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `scoreMin` | number | No | Filter by minimum score |
| `scoreMax` | number | No | Filter by maximum score |
| `completedBy` | string | No | Filter by user ID who completed audit |
| `completedByGroup` | string | No | Filter by user group ID |
| `templateId` | string | No | Filter by audit template ID |
| `auditObjectId` | string | No | Filter by audit object ID |
| `auditObjectGroupId` | string | No | Filter by audit object group ID |
| `assignedTo` | string | No | Filter by assigned user ID |
| `assignedToGroup` | string | No | Filter by assigned user group ID |
| `fromDate` | string | No | Filter by audit completion date (UTC format: `yyyy-MM-ddTHH:mm:ss.fffZ`) |
| `toDate` | string | No | Filter by audit completion date (UTC format: `yyyy-MM-ddTHH:mm:ss.fffZ`) |
| `pageNumber` | number | No | Current page number, starts from 1 (default: 1) |
| `pageSize` | number | No | Page size (default: 100) |

**Note:** This method will return an empty data list if the requested page does not exist.

### Example Request

```http
GET /audit/complete?scoreMin=80&pageSize=50
Host: api-external.monitorqa.com
X-API-KEY: abcdef12345
```

## Response

**Success Response**

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "data": [
    {
      "id": "a1b2c3d4-e5f6-789a-bcde-f01234567890",
      "name": "Quarterly Food Safety Audit",
      "assignees": [
        {
          "id": "b2c3d4e5-f6a7-890b-cdef-012345678901",
          "name": "Sarah Martinez"
        }
      ],
      "auditObject": {
        "id": "c3d4e5f6-a7b8-901c-defa-123456789012",
        "name": "Restaurant Main Kitchen"
      },
      "endDate": "2023-11-10T16:00:00.000Z",
      "number": "AUD-2023-Q4-001",
      "startDate": "2023-11-10T08:00:00.000Z",
      "template": {
        "id": "d4e5f6a7-b8c9-012d-efab-234567890123",
        "name": "Food Safety & Hygiene Checklist"
      },
      "completeDate": "2023-11-10T15:42:18.750Z",
      "completedBy": {
        "id": "b2c3d4e5-f6a7-890b-cdef-012345678901",
        "name": "Sarah Martinez"
      },
      "score": 94,
      "scoreLabel": "Excellent"
    },
    {
      "id": "e5f6a7b8-c9d0-123e-fabc-345678901234",
      "name": "Monthly Equipment Inspection",
      "assignees": [
        {
          "id": "f6a7b8c9-d0e1-234f-abcd-456789012345",
          "name": "James Wilson"
        },
        {
          "id": "a7b8c9d0-e1f2-345a-bcde-567890123456",
          "name": "Lisa Chen"
        }
      ],
      "auditObject": {
        "id": "b8c9d0e1-f2a3-456b-cdef-678901234567",
        "name": "Production Line A"
      },
      "endDate": "2023-11-08T17:30:00.000Z",
      "number": "AUD-2023-1156",
      "startDate": "2023-11-08T09:00:00.000Z",
      "template": {
        "id": "c9d0e1f2-a3b4-567c-defa-789012345678",
        "name": "Manufacturing Equipment Safety Audit"
      },
      "completeDate": "2023-11-08T16:55:30.250Z",
      "completedBy": {
        "id": "f6a7b8c9-d0e1-234f-abcd-456789012345",
        "name": "James Wilson"
      },
      "score": 82,
      "scoreLabel": "Good"
    }
  ],
  "meta": {
    "pageNumber": 1,
    "pageSize": 50,
    "totalCount": 2
  }
}
```

For errors responses, see the [response status codes documentation](#/response-status-codes).
