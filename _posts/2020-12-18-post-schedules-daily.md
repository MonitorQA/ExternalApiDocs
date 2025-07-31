---
category: 3. Schedules
url_path: '/schedules/daily'
title: 'Create daily schedule'
type: 'POST'
order: 14
layout: null
---

Create a daily recurring schedule that generates audits at specified intervals. This endpoint allows you to set up automated audit creation for designated users, audit objects, and templates on a daily basis.

## Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| templateId | string | Yes | The unique identifier of the audit template to use |
| auditObjectIds | array[string] | Conditional | Array of audit object IDs (required if auditObjectGroupIds not provided) |
| auditObjectGroupIds | array[string] | Conditional | Array of audit object group IDs (required if auditObjectIds not provided) |
| name | string | Yes | Display name for the schedule |
| auditorHint | string | No | Hint text visible to auditors during the audit (max 2000 characters) |
| assigneesIds | array[string] | No | Array of user IDs to assign the generated audits to |
| repeatEvery | integer | Yes | Interval in days between audit creation (range: 1-10) |
| active | boolean | No | Schedule status (defaults to `true`) |
| startFromDate | string | No | UTC date when schedule should start (format: `yyyy-MM-ddTHH:mm:ss.fffZ`) |
| stopByDate | string | No | UTC date after which schedule should stop (format: `yyyy-MM-ddTHH:mm:ss.fffZ`) |

## Request Example

```http
POST https://api-external.monitorqa.com/schedules/daily
X-API-KEY: abcdef12345
Content-Type: application/json

{
  "templateId": "template-123",
  "auditObjectIds": [
    "object-456",
    "object-789"
  ],
  "name": "Daily Safety Inspections",
  "auditorHint": "Focus on emergency exits and safety equipment",
  "assigneesIds": [
    "user-abc",
    "user-def"
  ],
  "repeatEvery": 1,
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
  "id": "schedule-xyz789"
}
```

For errors responses, see the [response status codes documentation](#/response-status-codes).
