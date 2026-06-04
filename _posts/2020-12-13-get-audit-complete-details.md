---
category: Audits
categoryOrder: 2
url_path: '/audit/complete/{auditId}'
title: 'Get details of complete audit'
type: 'GET'
order: 2
layout: null
---

Retrieve comprehensive details of a **completed** audit. The response uses the same field layout as [Get details of audit](#/get-audit-details), but this route sets `reportUrl`, `ianaTimeZone`, `auditorSignature`, and `auditeeSignature` when applicable.

### Request Headers

| Header | Type | Required | Description |
|--------|------|----------|-------------|
| `X-API-KEY` | string | Yes | API authentication key |

### Path Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `auditId` | uuid | Yes | Unique identifier of the completed audit |

### Example Request

```http
GET /audit/complete/{auditId}
Host: api-external.monitorqa.com
X-API-KEY: abcdef12345
```

## Response

**Success Response**

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "id": "a1b2c3d4-e5f6-789a-bcde-f01234567890",
  "companyId": "b2c3d4e5-f6a7-890b-cdef-012345678901",
  "number": "AUD-2023-0475",
  "name": "Cold Storage Compliance Audit - Oct 2023",
  "auditorHint": "Pay special attention to cold storage temperature logs and cleaning schedules",
  "auditObject": {
    "id": "c3d4e5f6-a7b8-901c-defa-123456789012",
    "name": "Warehouse Cold Storage Unit B",
    "notes": "Temperature-controlled environment for perishable goods"
  },
  "startedBy": {
    "id": "d4e5f6a7-b8c9-012d-efab-234567890123",
    "name": "Michael Johnson"
  },
  "templateId": "e5f6a7b8-c9d0-123e-fabc-345678901234",
  "template": {
    "id": "e5f6a7b8-c9d0-123e-fabc-345678901234",
    "name": "Cold Storage Compliance Audit"
  },
  "assignees": [
    {
      "id": "f6a7b8c9-d0e1-234f-abcd-456789012345",
      "name": "Rachel Kim"
    },
    {
      "id": "a7b8c9d0-e1f2-345a-bcde-567890123456",
      "name": "Carlos Rodriguez"
    }
  ],
  "isStarted": true,
  "isFailed": false,
  "startedAt": "2023-10-25T07:30:00.000Z",
  "isCompleted": true,
  "completeDate": "2023-10-25T11:45:33.875Z",
  "isExpired": false,
  "isReopened": false,
  "completedBy": {
    "id": "f6a7b8c9-d0e1-234f-abcd-456789012345",
    "name": "Rachel Kim"
  },
  "startDate": "2023-10-25T07:00:00.000Z",
  "endDate": "2023-10-25T15:00:00.000Z",
  "score": 91,
  "scoreLabel": "Excellent",
  "scoreColor": "#198754",
  "durationInSeconds": 255,
  "ianaTimeZone": "America/New_York",
  "reportUrl": "https://reports.example.com/audit/a1b2c3d4-e5f6-789a-bcde-f01234567890",
  "auditeeSignature": {
    "photoId": "d1b4b954-3e9f-4d93-bdeb-a4112f1ed26e",
    "createdBy": {
      "id": "00000000-0000-0000-0000-000000000000",
      "name": "Auditee name"
    }
  },
  "auditorSignature": {
    "photoId": "c54e4562-3ce2-4957-b1f0-2dd96405de29",
    "createdBy": {
      "id": "3c71b2a5-4c01-4bb0-9f08-785a2d8f7128",
      "name": "Rachel Kim"
    }
  }
}
```

### Response fields

Same field set as [Get details of audit](#/get-audit-details). On this route, `reportUrl`, `ianaTimeZone`, `auditorSignature`, and `auditeeSignature` are populated for completed audits when data exists. For `auditeeSignature.createdBy`, only `name` may be populated.

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
| `reportUrl` | string | URL to the audit report (public or authorized, depending on template and token) |
| `auditeeSignature` | object | Optional. `photoId` (uuid), `createdBy` (`id`, `name`) |
| `auditorSignature` | object | Optional. `photoId` (uuid), `createdBy` (`id`, `name`) |

For errors responses, see the [response status codes documentation](#/response-status-codes).

