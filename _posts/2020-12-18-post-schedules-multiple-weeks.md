---
category: 3. Schedules
categoryOrder: 3
url_path: '/schedules/multiple-weeks'
title: 'Create multiple weeks schedule'
type: 'POST'
order: 5
layout: null
---

Create a multi-week recurring schedule that generates audits at specified weekly intervals on a particular day of the week. This endpoint enables setting up automated audit creation with flexible multi-week recurrence patterns.

## Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| templateId | string | Yes | The unique identifier of the audit template to use |
| auditObjectIds | array[string] | Conditional | Array of audit object IDs (required if auditObjectGroupIds not provided) |
| auditObjectGroupIds | array[string] | Conditional | Array of audit object group IDs (required if auditObjectIds not provided) |
| name | string | Yes | Display name for the schedule |
| auditorHint | string | No | Hint text visible to auditors during the audit (max 2000 characters) |
| assigneesIds | array[string] | No | Array of user IDs to assign the generated audits to |
| repeatEvery | integer | Yes | Interval in weeks between audit creation |
| startDay | integer | Yes | Day of the week to start audits (0=Sunday, 1=Monday, 2=Tuesday, 3=Wednesday, 4=Thursday, 5=Friday, 6=Saturday) |
| duration | integer | Yes | Audit duration in days (1 to repeatEvery×7) |
| active | boolean | No | Schedule status (defaults to `true`) |
| startFromDate | string | No | UTC date when schedule should start (format: `yyyy-MM-ddTHH:mm:ss.fffZ`) |
| stopByDate | string | No | UTC date after which schedule should stop (format: `yyyy-MM-ddTHH:mm:ss.fffZ`) |

### Example Request

```http
POST /schedules/multiple-weeks
Host: api-external.monitorqa.com
X-API-KEY: abcdef12345
Content-Type: application/json

{
  "templateId": "123e4567-e89b-12d3-a456-426614174000",
  "auditObjectIds": [
    "456e7890-e89b-12d3-a456-426614174000",
    "789e0123-e89b-12d3-a456-426614174000"
  ],
  "name": "Bi-weekly Equipment Check",
  "auditorHint": "Check all safety equipment and machinery",
  "assigneesIds": [
    "abc12345-e89b-12d3-a456-426614174000",
    "def67890-e89b-12d3-a456-426614174000"
  ],
  "repeatEvery": 2,
  "startDay": 1,
  "duration": 3,
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
  "id": "901234op-qrst-567g-hijk-678901234567"
}
```

For errors responses, see the [response status codes documentation](#/response-status-codes).
