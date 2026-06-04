---
category: Audits
categoryOrder: 2
url_path: '/audit/{auditId}'
title: 'Get details of audit'
type: 'GET'
order: 2
layout: null
---

Retrieve detailed information about a specific audit by ID. The response body is a single audit resource; field definitions and the example below describe the JSON shape. For **completed** audits, prefer [Get details of complete audit](#/get-audit-complete-details) if you need `reportUrl` and signature objects populated.

### Request Headers

| Header | Type | Required | Description |
|--------|------|----------|-------------|
| `X-API-KEY` | string | Yes | API authentication key |

### Path Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `auditId` | uuid | Yes | Unique identifier of the audit |

### Example Request

```http
GET /audit/123e4567-e89b-12d3-a456-426614174000
Host: api-external.monitorqa.com
X-API-KEY: abcdef12345
```

## Response

**Success Response**

This action returns all fields documented for the audit resource below. `reportUrl`, `auditorSignature`, and `auditeeSignature` are **not** set by this endpoint and appear as `null` in JSON when present.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "id": "a1b2c3d4-e5f6-789a-bcde-f01234567890",
  "companyId": "b2c3d4e5-f6a7-890b-cdef-012345678901",
  "number": "AUD-2023-0892",
  "name": "Fire Safety and Emergency Preparedness Audit - Nov 2023",
  "auditorHint": "Check all emergency exits are clear and properly marked",
  "auditObject": {
    "id": "c3d4e5f6-a7b8-901c-defa-123456789012",
    "name": "Corporate Headquarters - Floor 3",
    "notes": "High traffic area with multiple conference rooms"
  },
  "startedBy": {
    "id": "d4e5f6a7-b8c9-012d-efab-234567890123",
    "name": "Jennifer Thompson"
  },
  "templateId": "e5f6a7b8-c9d0-123e-fabc-345678901234",
  "template": {
    "id": "e5f6a7b8-c9d0-123e-fabc-345678901234",
    "name": "Fire Safety and Emergency Preparedness Audit"
  },
  "assignees": [
    {
      "id": "f6a7b8c9-d0e1-234f-abcd-456789012345",
      "name": "David Lee"
    },
    {
      "id": "a7b8c9d0-e1f2-345a-bcde-567890123456",
      "name": "Amanda Rodriguez"
    }
  ],
  "isStarted": true,
  "startedAt": "2023-11-15T09:30:00.000Z",
  "isCompleted": true,
  "completeDate": "2023-11-15T14:45:22.150Z",
  "isFailed": false,
  "isExpired": false,
  "isReopened": false,
  "completedBy": {
    "id": "f6a7b8c9-d0e1-234f-abcd-456789012345",
    "name": "David Lee"
  },
  "startDate": "2023-11-15T09:00:00.000Z",
  "endDate": "2023-11-15T17:00:00.000Z",
  "score": 87,
  "scoreLabel": "Good",
  "scoreColor": "#28a745",
  "durationInSeconds": 315,
  "ianaTimeZone": "America/New_York",
  "reportUrl": null,
  "auditeeSignature": null,
  "auditorSignature": null
}
```

### Response fields

| Field | Type | Description |
|-------|------|-------------|
| `id` | uuid | Audit identifier |
| `companyId` | uuid | Company identifier |
| `number` | string | Audit number |
| `name` | string | Audit display name |
| `auditorHint` | string | Hint for auditors |
| `auditObject` | object | `id` (uuid), `name` (string), `notes` (string) |
| `startedBy` | object | Optional. `id` (uuid), `name` (string) |
| `templateId` | uuid | Template identifier |
| `template` | object | `id` (uuid), `name` (string) |
| `assignees` | array | Assigned users; each item `id` (uuid), `name` (string) |
| `isStarted` | boolean | Whether the audit has been started |
| `startedAt` | string (UTC) | Optional. When the audit was started |
| `isCompleted` | boolean | Whether the audit is completed |
| `completeDate` | string (UTC) | Optional. Completion timestamp |
| `isReopened` | boolean | Whether the audit was reopened |
| `completedBy` | object | Optional. `id` (uuid), `name` (string) |
| `startDate` | string (UTC) | Optional. Scheduled start |
| `endDate` | string (UTC) | Optional. Scheduled end |
| `score` | number | Optional. Numeric score |
| `scoreLabel` | string | Optional. Score label |
| `scoreColor` | string | Optional. Score color (CSS color) |
| `durationInSeconds` | integer | Duration in seconds |
| `ianaTimeZone` | string | IANA time zone for local timestamps |
| `isExpired` | boolean | Whether the audit is expired |
| `isFailed` | boolean | Optional. Whether the audit failed |
| `reportUrl` | string | Optional. Not set by this route (use complete-audit details for report URL) |
| `auditeeSignature` | object | Optional. Not set by this route. When set: `photoId` (uuid), `createdBy` (`id`, `name`) |
| `auditorSignature` | object | Optional. Not set by this route. When set: `photoId` (uuid), `createdBy` (`id`, `name`) |

For errors responses, see the [response status codes documentation](#/response-status-codes).

