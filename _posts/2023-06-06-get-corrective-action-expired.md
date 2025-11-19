---
category: 9. Corrective Actions
url_path: '/corrective-actions/expired'
title: 'Get expired corrective actions list'
type: 'GET'
order: 9
layout: null
---

Retrieve a paginated list of expired corrective actions within your organization. This endpoint provides access to corrective actions that have passed their due dates without completion, helping track overdue items.

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

**Note:** This method will return an empty data list if the requested page does not exist.

### Example Request

```http
GET /corrective-actions/expired?pageNumber=1&pageSize=10
Host: api-external.monitorqa.com
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
      "id": "567890kl-mnop-123c-defg-234567890123",
      "name": "Update Safety Signage",
      "number": "CA-2024-003",
      "assignedUsers": [
        {
          "id": "123e4567-e89b-12d3-a456-426614174000",
          "name": "Bob Maintenance"
        }
      ],
      "audit": {
        "id": "789012mn-opqr-345e-fghi-456789012345",
        "name": "Facility Safety Audit",
        "ianaTimeZone": "America/New_York",
        "number": "AUD-2024-003"
      },
      "createdBy": {
        "id": "456e7890-e89b-12d3-a456-426614174002",
        "name": "Alice Inspector"
      },
      "auditObject": {
        "id": "234567890-abcd-efgh-ijkl-mnopqrstuvwx",
        "name": "Building B Entrance"
      },
      "status": 4,
      "priority": 1,
      "createdAtUtc": "2024-01-05T08:00:00.000Z",
      "dueDateUtc": "2024-01-20T17:00:00.000Z",
      "expiredBy": {
        "id": "000000000-0000-0000-0000-000000000000",
        "name": "System Auto-Expire"
      },
      "expiredAtUtc": "2024-01-21T00:00:00.000Z"
    }
  ],
  "meta": {
    "pageNumber": 1,
    "pageSize": 10,
    "totalCount": 1
  }
}
```

For errors responses, see the [response status codes documentation](#/response-status-codes).
