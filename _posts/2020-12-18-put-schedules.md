---
category: 3. Schedules
url_path: '/schedules/{scheduleId}'
title: 'Update schedule'
type: 'PUT'
order: 18
layout: null
---

Update an existing schedule's configuration, including audit objects, assignments, and recurrence patterns. This endpoint allows you to modify all aspects of a schedule except its template.

## Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| scheduleId | string | Yes | The unique identifier of the schedule to update |
| auditObjectIds | array[string] | Conditional | Array of audit object IDs (required if auditObjectGroupIds not provided) |
| auditObjectGroupIds | array[string] | Conditional | Array of audit object group IDs (required if auditObjectIds not provided) |
| name | string | Yes | Display name for the schedule |
| auditorHint | string | No | Hint text visible to auditors during the audit (max 2000 characters) |
| assigneesIds | array[string] | No | Array of user IDs to assign the generated audits to |
| repeatPattern | integer | Yes | Schedule repeat pattern (0=One-time, 1=Daily, 2=Multiple Weeks, 3=Monthly, 4=Weekly) |
| repeat | object | Yes | Repeat configuration options (varies by repeatPattern) |
| active | boolean | No | Schedule status (defaults to `true`, ignored for one-time schedules) |
| startFromDate | string | No | UTC date when schedule should start (format: `yyyy-MM-ddTHH:mm:ss.fffZ`, ignored for one-time) |
| stopByDate | string | No | UTC date after which schedule should stop (format: `yyyy-MM-ddTHH:mm:ss.fffZ`, ignored for one-time) |

## Repeat Pattern Options

### One-time (repeatPattern: 0)
```json
{
  "startDate": "2024-02-01T08:00:00.000Z",
  "endDate": "2024-02-15T17:00:00.000Z"
}
```

### Daily (repeatPattern: 1)
```json
{
  "repeatEvery": 3
}
```

### Multiple Weeks (repeatPattern: 2)
```json
{
  "repeatEvery": 2,
  "startDay": 1,
  "duration": 5
}
```

### Monthly (repeatPattern: 3)
```json
{
  "repeatEvery": 1,
  "startDay": 15,
  "duration": 7
}
```

### Weekly (repeatPattern: 4)
```json
{
  "daysOfWeek": [1, 3, 5]
}
```

### Example Request

```http
PUT /schedules/456e7890-e89b-12d3-a456-426614174000
Host: api-external.monitorqa.com
X-API-KEY: abcdef12345
Content-Type: application/json

{
  "auditObjectIds": [
    "456e7890-e89b-12d3-a456-426614174000",
    "789e0123-e89b-12d3-a456-426614174000"
  ],
  "name": "Updated Daily Safety Check",
  "auditorHint": "Updated instructions: Focus on new safety protocols",
  "assigneesIds": [
    "abc12345-e89b-12d3-a456-426614174000",
    "def67890-e89b-12d3-a456-426614174000"
  ],
  "repeatPattern": 1,
  "repeat": {
    "repeatEvery": 2
  },
  "active": true,
  "startFromDate": "2024-02-01T08:00:00.000Z",
  "stopByDate": "2024-12-31T23:59:59.000Z"
}
```

## Response

**Success Response**

```http
HTTP/1.1 200 OK
```

Empty response body indicates successful schedule update.

For errors responses, see the [response status codes documentation](#/response-status-codes).
