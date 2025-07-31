---
category: 3. Schedules
url_path: '/schedules/{scheduleId}/status'
title: '[DEPRECATED] Set schedule status'
type: 'POST'
order: 21
layout: null
---

**[DEPRECATED]** This endpoint allows you to modify the status of existing schedules in the MonitorQA system. Use this to activate, deactivate, or set future activation/deactivation dates for schedules. Note that this method cannot be used with one-time schedules.

## Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| scheduleId | string | Yes | The unique identifier of the schedule to modify |
| active | boolean | Yes | Set to `true` to activate or `false` to deactivate the schedule |
| stopByDate | string | No | UTC date after which the schedule should be stopped (format: `yyyy-MM-ddTHH:mm:ss.fffZ`) |
| startFromDate | string | No | UTC date when the schedule should be started (format: `yyyy-MM-ddTHH:mm:ss.fffZ`) |

## Request Examples

### Disable schedule with optional future activation

```http
POST https://api-external.monitorqa.com/schedules/{scheduleId}/status
X-API-KEY: abcdef12345
Content-Type: application/json

{
  "active": false,
  "startFromDate": "2024-12-31T09:00:00.000Z"
}
```

### Enable schedule with optional future deactivation

```http
POST https://api-external.monitorqa.com/schedules/{scheduleId}/status
X-API-KEY: abcdef12345
Content-Type: application/json

{
  "active": true,
  "stopByDate": "2025-06-30T23:59:59.000Z"
}
```

## Response

**Success Response**

```http
HTTP/1.1 200 OK
```

Empty response body indicates successful status update.

For errors responses, see the [response status codes documentation](#/response-status-codes).
