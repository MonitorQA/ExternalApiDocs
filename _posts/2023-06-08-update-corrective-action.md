---
category: Corrective Actions
categoryOrder: 10
url_path: '/corrective-actions/{id}'
title: 'Update corrective action details'
type: 'PUT'
order: 5
layout: null
---

Update the details of an existing corrective action. This endpoint enables modifying corrective action properties including assignments, due dates, status, and priority levels.

## Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| id | string | Yes | The unique identifier of the corrective action to update |
| assignedUsersIds | array[string] | No | Array of user IDs to assign the corrective action to |
| description | string | No | Detailed description of the corrective action |
| name | string | Yes | Name/title of the corrective action |
| dueDateUtc | string | Yes | Due date in UTC format (`yyyy-MM-ddTHH:mm:ss.fffZ`) |
| status | integer | Yes | Status code (0=Open, 1=Approved, 2=Rejected, 3=Submitted, 4=Expired) |
| priority | integer | Yes | Priority level (0=Low, 1=Medium, 2=High) |

### Example Request

```http
PUT /corrective-actions/{id}
Host: api-external.monitorqa.com
X-API-KEY: abcdef12345
Content-Type: application/json

{
  "assignedUsersIds": ["123e4567-e89b-12d3-a456-426614174000", "987fcdeb-51d2-43e8-b456-426614174001"],
  "description": "Replace damaged safety equipment and conduct training",
  "name": "Safety Equipment Replacement",
  "dueDateUtc": "2024-02-15T17:00:00.000Z",
  "status": 3,
  "priority": 2
}
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
```

Empty response body indicates successful corrective action update.


For errors responses, see the [response status codes documentation](#/response-status-codes).
