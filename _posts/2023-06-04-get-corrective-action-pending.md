---
category: 9. Corrective Actions
url_path: '/corrective-actions/pending'
title: 'Get pending corrective actions list'
type: 'GET'
order: 1
layout: null
---

Retrieve a paginated list of pending corrective actions within your organization. This endpoint allows you to filter results by various criteria and provides comprehensive details about each corrective action requiring attention.

## Query Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| auditId | string | No | Filter by specific audit ID |
| templateId | string | No | Filter by audit template ID |
| auditObjectId | string | No | Filter by audit object ID |
| assignedToId | string | No | Filter by assigned user ID |
| assignedToGroupId | string | No | Filter by assigned user group ID |
| fromDate | string | No | Filter by due date from (UTC format: `yyyy-MM-ddTHH:mm:ss.fffZ`) |
| toDate | string | No | Filter by due date to (UTC format: `yyyy-MM-ddTHH:mm:ss.fffZ`) |
| pageNumber | integer | No | Page number for pagination (starts from 1) |
| pageSize | integer | No | Number of items per page |

## Request Example

```http
GET https://api-external.monitorqa.com/corrective-actions/pending?pageNumber=1&pageSize=10&assignedToId=user-123
X-API-KEY: abcdef12345
```

## Response

### Status Codes
- `0` - Open
- `1` - Approved
- `2` - Rejected
- `3` - Submitted
- `4` - Expired

### Priority Levels
- `0` - Low
- `1` - Medium
- `2` - High

**Success Response**

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "data": [
    {
      "id": "ca-123",
      "assignedUsers": [
        {
          "id": "user-456",
          "name": "John Smith"
        }
      ],
      "audit": {
        "id": "audit-789",
        "name": "Safety Inspection",
        "ianaTimeZone": "America/New_York",
        "number": "AUD-2024-001"
      },
      "createdBy": {
        "id": "user-manager",
        "name": "Jane Manager"
      },
      "auditObject": {
        "id": "object-facility",
        "name": "Main Production Floor"
      },
      "status": 0,
      "priority": 1,
      "createdAtUtc": "2024-01-15T10:30:00.000Z",
      "dueDateUtc": "2024-02-01T17:00:00.000Z",
      "name": "Fix Safety Guard",
      "number": "CA-2024-001"
    }
  ],
  "meta": {
    "pageNumber": 1,
    "pageSize": 10,
    "totalCount": 25
  }
}
```


For errors responses, see the [response status codes documentation](#/response-status-codes).
