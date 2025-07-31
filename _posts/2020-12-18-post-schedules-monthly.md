---
category: 3. Schedules
url_path: '/schedules/monthly'
title: 'Create monthly schedule'
type: 'POST'
order: 17
layout: null
---

Create a monthly recurring schedule that generates audits at specified intervals on a particular day of the month. This endpoint allows you to set up automated audit creation with flexible monthly recurrence patterns.

## Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| templateId | string | Yes | The unique identifier of the audit template to use |
| auditObjectIds | array[string] | Conditional | Array of audit object IDs (required if auditObjectGroupIds not provided) |
| auditObjectGroupIds | array[string] | Conditional | Array of audit object group IDs (required if auditObjectIds not provided) |
| name | string | Yes | Display name for the schedule |
| auditorHint | string | No | Hint text visible to auditors during the audit (max 2000 characters) |
| assigneesIds | array[string] | No | Array of user IDs to assign the generated audits to |
| repeatEvery | integer | Yes | Interval in months between audit creation |
| startDay | integer | Yes | Day of the month to start audits (1-31, uses last day if date doesn't exist) |
| duration | integer | Yes | Audit duration in days (1 to repeatEvery×31) |
| active | boolean | No | Schedule status (defaults to `true`) |
| startFromDate | string | No | UTC date when schedule should start (format: `yyyy-MM-ddTHH:mm:ss.fffZ`) |
| stopByDate | string | No | UTC date after which schedule should stop (format: `yyyy-MM-ddTHH:mm:ss.fffZ`) |

## Request Example

```http
POST https://api-external.monitorqa.com/schedules/monthly
X-API-KEY: abcdef12345
Content-Type: application/json

{
  "templateId": "template-123",
  "auditObjectIds": [
    "object-456",
    "object-789"
  ],
  "name": "Monthly Compliance Review",
  "auditorHint": "Review all compliance documentation and procedures",
  "assigneesIds": [
    "user-abc",
    "user-def"
  ],
  "repeatEvery": 1,
  "startDay": 15,
  "duration": 7,
  "active": true,
  "startFromDate": "2024-01-01T08:00:00.000Z",
  "stopByDate": "2024-12-31T23:59:59.000Z"
}
```

## Response

**Success Response**

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "id": "schedule-monthly-xyz"
}
```

For errors responses, see the [response status codes documentation](#/response-status-codes).
