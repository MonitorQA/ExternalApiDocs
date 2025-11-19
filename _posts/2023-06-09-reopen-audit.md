---
category: 2. Audits
url_path: '/audit/reopen/{id}'
title: 'Reopen Audit'
type: 'POST'
order: 2
layout: null
---

Reopen a completed audit to allow additional work or corrections. This endpoint enables you to restore a completed audit to an active state with new dates and optionally reassign it to different users.

## Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| id | string | Yes | The unique identifier of the completed audit to reopen |
| startDate | string | Yes | New start date in UTC format (`yyyy-MM-ddTHH:mm:ss.fffZ`) |
| endDate | string | Yes | New due date in UTC format (`yyyy-MM-ddTHH:mm:ss.fffZ`) |
| assigneesIds | array[string] | No | Array of user IDs to assign the audit to (null = no change, empty array = remove all assignees) |

### Example Request

```http
POST /audit/reopen/123e4567-e89b-12d3-a456-426614174000
Host: api-external.monitorqa.com
X-API-KEY: abcdef12345
Content-Type: application/json

{
  "assigneesIds": [
    "456e7890-e89b-12d3-a456-426614174000",
    "789e0123-e89b-12d3-a456-426614174000"
  ],
  "startDate": "2024-02-01T08:00:00.000Z",
  "endDate": "2024-02-15T17:00:00.000Z"
}
```

## Response

**Success Response**

```http
HTTP/1.1 200 OK
```

Empty response body indicates successful reopening of the audit.

For errors responses, see the [response status codes documentation](#/response-status-codes).
