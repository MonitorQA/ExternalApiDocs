---
category: 3. Schedules
url_path: '/schedules/ad-hoc'
title: '[DEPRECATED] Create ad-hoc audit'
type: 'POST'
order: 12
layout: null
---
**THIS METHOD WILL BE REPLACED WITH [Create one-time audit](#/post-audit)**

This method allows you to create an ad-hoc audit for a specified user. Note that this method is deprecated and will be replaced with the [Create one-time audit](#/post-audit) endpoint.

### Request Headers

| Header | Type | Required | Description |
|--------|------|----------|-------------|
| `X-API-KEY` | string | Yes | Your API authentication key |
| `Content-Type` | string | Yes | Must be `application/json` |

### Request Body Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `date` | string | Yes | Audit local due date (format: `yyyy-MM-ddTHH:mm:ss.fffZ`) |
| `name` | string | Yes | Schedule name |
| `auditorHint` | string | No | Auditor hint visible during audit (max 2000 characters) |
| `templateId` | string | Yes | Audit template ID |
| `auditObjectId` | string | Yes | Audit object ID |
| `userId` | string | No | User ID to assign audit to |

### Example Request

```http
POST /schedules/ad-hoc
Host: api-external.monitorqa.com
X-API-KEY: abcdef12345
Content-Type: application/json

{
  "name": "Emergency Safety Audit",
  "auditorHint": "Focus on fire safety equipment and emergency exits",
  "date": "2025-07-31T15:30:00.000Z",
  "templateId": "123e4567-e89b-12d3-a456-426614174000",
  "auditObjectId": "987f6543-a21b-43c5-d654-321987654321",
  "userId": "456a7890-b12c-34d5-e678-901234567890"
}
```

## Response

**Success Response**

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "id": "string"
}```

For errors responses, see the [response status codes documentation](#/response-status-codes).
