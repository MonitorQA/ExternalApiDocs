---
category: 3. Schedules
url_path: '/schedules/one-time'
title: 'Create one-time schedule'
type: 'POST'
order: 13
layout: null
---

Create a one-time schedule that generates a single audit for specified users and objects. This endpoint is ideal for ad-hoc audits or special inspections that don't require recurring schedules.

## Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| templateId | string | Yes | The unique identifier of the audit template to use |
| auditObjectIds | array[string] | Conditional | Array of audit object IDs (required if auditObjectGroupIds not provided) |
| auditObjectGroupIds | array[string] | Conditional | Array of audit object group IDs (required if auditObjectIds not provided) |
| name | string | Yes | Display name for the schedule |
| auditorHint | string | No | Hint text visible to auditors during the audit (max 2000 characters) |
| assigneesIds | array[string] | No | Array of user IDs to assign the generated audit to |
| startDate | string | No | UTC date when the audit should start (format: `yyyy-MM-ddTHH:mm:ss.fffZ`) |
| endDate | string | Yes | UTC date when the audit is due (format: `yyyy-MM-ddTHH:mm:ss.fffZ`) |

## Request Example

```http
POST https://api-external.monitorqa.com/schedules/one-time
X-API-KEY: abcdef12345
Content-Type: application/json

{
  "templateId": "template-123",
  "auditObjectIds": [
    "object-456",
    "object-789"
  ],
  "name": "Special Safety Inspection",
  "auditorHint": "Focus on recent incident area and emergency procedures",
  "assigneesIds": [
    "user-abc"
  ],
  "startDate": "2024-02-01T08:00:00.000Z",
  "endDate": "2024-02-15T17:00:00.000Z"
}
```

## Response

**Success Response**

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "id": "schedule-onetime-xyz"
}
```

For errors responses, see the [response status codes documentation](#/response-status-codes).
