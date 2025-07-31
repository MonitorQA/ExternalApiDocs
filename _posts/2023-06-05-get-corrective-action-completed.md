---
category: 9. Corrective Actions
url_path: '/corrective-actions/completed'
title: 'Get completed corrective actions list'
type: 'GET'
order: 2
layout: null
---

Retrieve a paginated list of completed corrective actions within your organization. This endpoint provides access to all approved corrective actions with detailed information about their completion status and approval details.

## Query Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| auditId | string | No | Filter by specific audit ID |
| templateId | string | No | Filter by audit template ID |
| auditObjectId | string | No | Filter by audit object ID |
| assignedToId | string | No | Filter by assigned user ID |
| approvedById | string | No | Filter by approver user ID |
| assignedToGroupId | string | No | Filter by assigned user group ID |
| fromDate | string | No | Filter by due date from (UTC format: `yyyy-MM-ddTHH:mm:ss.fffZ`) |
| toDate | string | No | Filter by due date to (UTC format: `yyyy-MM-ddTHH:mm:ss.fffZ`) |
| pageNumber | integer | No | Page number for pagination (starts from 1) |
| pageSize | integer | No | Number of items per page |

## Request Example

```http
GET https://api-external.monitorqa.com/corrective-actions/completed?pageNumber=1&pageSize=10&approvedById=user-manager
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
      "id": "ca-456",
      "name": "Replace Safety Equipment",
      "number": "CA-2024-002",
      "assignedUsers": [
        {
          "id": "user-789",
          "name": "Mike Wilson"
        }
      ],
      "audit": {
        "id": "audit-123",
        "name": "Monthly Safety Check",
        "ianaTimeZone": "America/New_York",
        "number": "AUD-2024-002"
      },
      "createdBy": {
        "id": "user-supervisor",
        "name": "Sarah Supervisor"
      },
      "auditObject": {
        "id": "object-warehouse",
        "name": "Warehouse Section A"
      },
      "status": 1,
      "priority": 0,
      "createdAtUtc": "2024-01-10T09:00:00.000Z",
      "dueDateUtc": "2024-01-25T17:00:00.000Z",
      "approvedBy": {
        "id": "user-manager",
        "name": "Jane Manager"
      },
      "approvedAtUtc": "2024-01-24T14:30:00.000Z"
    }
  ],
  "meta": {
    "pageNumber": 1,
    "pageSize": 10,
    "totalCount": 15
  }
}
```


For errors responses, see the [response status codes documentation](#/response-status-codes).
