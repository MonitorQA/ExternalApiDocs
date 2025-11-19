---
category: 2. Audits
url_path: '/audit'
title: 'Create one-time audit'
type: 'POST'
order: 2
layout: null
---

Create a one-time audit for a specific user and audit object. This endpoint is useful for creating immediate audit tasks that need to be completed by a particular person.

### Request Headers

| Header | Type | Required | Description |
|--------|------|----------|-------------|
| `X-API-KEY` | string | Yes | API authentication key |

### Request Body Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `startDate` | datetime | No | Local start date for the audit. If not provided, audit can be started immediately |
| `endDate` | datetime | Yes | Local due date when the audit must be completed |
| `name` | string | Yes | Name of the audit for identification purposes |
| `auditorHint` | string | No | Helpful hint or instructions visible to the auditor during audit execution (max 2000 characters) |
| `templateId` | string | Yes | Unique identifier of the audit template to use |
| `auditObjectId` | string | Yes | Unique identifier of the audit object to be audited |
| `assigneeId` | string | No | Unique identifier of the user who will perform the audit |

### Example Request

```http
POST /audit
Host: api-external.monitorqa.com
X-API-KEY: abcdef12345
Content-Type: application/json

{
  "startDate": "2024-01-15T08:00:00.000Z",
  "endDate": "2024-01-15T18:00:00.000Z",
  "name": "Weekly Safety Inspection",
  "auditorHint": "Focus on emergency exits and fire safety equipment",
  "templateId": "123e4567-e89b-12d3-a456-426614174000",
  "auditObjectId": "789e0123-e89b-12d3-a456-426614174000",
  "assigneeId": "456e7890-e89b-12d3-a456-426614174000"
}
```

## Response

**Success Response**

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "id": "a1b2c3d4-e5f6-789a-bcde-f01234567890"
}
```

For errors responses, see the [response status codes documentation](#/response-status-codes).
