---
category: 2. Audits
url_path: '/audit'
title: 'Create one-time audit'
type: 'POST'
order: 1
layout: null
---

This method allows you to create a one-time audit for a specific user and audit object. This is useful for creating immediate audit tasks that need to be completed by a particular person.

### Request Headers

| Header | Type | Required | Description |
|--------|------|----------|-------------|
| `X-API-KEY` | string | Yes | Your API authentication key |

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

### Response

**If succeeds**, returns an id of created audit.

```Status: 200 OK```

```{
  "id": "string"
}```

For errors responses, see the [response status codes documentation](#/response-status-codes).
