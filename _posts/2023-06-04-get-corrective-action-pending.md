---
category: Corrective Actions
categoryOrder: 10
url_path: '/corrective-actions/pending'
title: 'Get pending corrective actions list'
type: 'GET'
order: 1
layout: null
---

Retrieve a paginated list of pending corrective actions within the organization. This endpoint enables filtering results by various criteria and provides comprehensive details about each corrective action requiring attention.

**Note:** To retrieve a list of available IANA time zones, use the [Get timezones](#/get-timezones) endpoint.

## Query Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| auditId | string | No | Filter by specific audit ID |
| templateId | string | No | Filter by audit template ID |
| auditObjectId | string | No | Filter by audit object ID |
| assignedToId | string | No | Filter by assigned user ID |
| assignedToGroupId | string | No | Filter by assigned user group ID |
| pageNumber | integer | No | Page number for pagination (starts from 1) |
| pageSize | integer | No | Number of items per page |

**Note:** This method will return an empty data list if the requested page does not exist.

### Example Request

```http
GET /corrective-actions/pending?pageNumber=1&pageSize=10&assignedToId=123e4567-e89b-12d3-a456-426614174000
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
      "assignedUsers": [
        {
          "id": "987fcdeb-51d2-43e8-b456-426614174001",
          "name": "John Smith"
        }
      ],
      "audit": {
        "id": "789012mn-opqr-345e-fghi-456789012345",
        "name": "Safety Inspection",
        "ianaTimeZone": "America/New_York",
        "number": "AUD-2024-001"
      },
      "createdBy": {
        "id": "456e7890-e89b-12d3-a456-426614174002",
        "name": "Jane Manager"
      },
      "auditObject": {
        "id": "234567890-abcd-efgh-ijkl-mnopqrstuvwx",
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
    "totalCount": 1
  }
}
```

For errors responses, see the [response status codes documentation](#/response-status-codes).
