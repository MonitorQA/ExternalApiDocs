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

### Example Request

```http
POST /schedules/one-time
Host: api-external.monitorqa.com
X-API-KEY: abcdef12345
Content-Type: application/json

{
  "templateId": "123e4567-e89b-12d3-a456-426614174000",
  "auditObjectIds": [
    "456e7890-e89b-12d3-a456-426614174000",
    "789e0123-e89b-12d3-a456-426614174000"
  ],
  "name": "Special Safety Inspection",
  "auditorHint": "Focus on recent incident area and emergency procedures",
  "assigneesIds": [
    "abc12345-e89b-12d3-a456-426614174000"
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
  "id": "234567op-qrst-567g-hijk-678901234568"
}
```

For errors responses, see the [response status codes documentation](#/response-status-codes).
