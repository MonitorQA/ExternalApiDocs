---
category: Corrective Actions
categoryOrder: 10
url_path: '/corrective-actions/{id}'
title: 'Get corrective action details'
type: 'GET'
order: 4
layout: null
---

Retrieve detailed information about a specific corrective action, including its status, assignees, files, and related audit information.

**Note:** To retrieve a list of available IANA time zones, use the [Get timezones](#/get-timezones) endpoint.

### Request Headers

| Header | Type | Required | Description |
|--------|------|----------|-------------|
| `X-API-KEY` | string | Yes | API authentication key |

### Path Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `id` | uuid | Yes | Unique identifier of the corrective action |

### Example Request

```http
GET /corrective-actions/123e4567-e89b-12d3-a456-426614174000
Host: api-external.monitorqa.com
X-API-KEY: abcdef12345
```

## Response

#### Status Values

| Value | Status | Description |
|-------|--------|-------------|
| `0` | Open | Corrective action is open and pending work |
| `1` | Approved | Corrective action has been approved |
| `2` | Rejected | Corrective action has been rejected |
| `3` | Submitted | Corrective action has been submitted for review |
| `4` | Expired | Corrective action has expired without completion |

#### Priority Values

| Value | Priority | Description |
|-------|----------|-------------|
| `0` | Low | Low priority corrective action |
| `1` | Medium | Medium priority corrective action |
| `2` | High | High priority corrective action |

**Success Response**

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
   "answer": {
      "name": "Fire extinguisher inspection",
      "points": 5,
      "text": "Fire extinguisher is missing from designated location",
      "number": 3,
      "isFailed": true
   },
   "approvedAtUtc": "2023-11-15T14:30:22.123Z",
   "approvedBy": {
        "id": "a8f3d2c1-b4e5-4f60-9080-1a2b3c4d5e6f",
        "name": "Sarah Johnson"
      },
   "assignedUsers": [
      {
         "id": "b9e4c3d2-c5f6-5670-8090-2a3b4c5d6e7f",
         "name": "Mike Rodriguez"
      }
   ],
   "audit": {
      "id": "c0f5d4e3-d607-6080-1a0b-3c4d5e6f7081",
      "name": "Monthly Safety Inspection - Building A",
      "ianaTimeZone": "America/New_York",
      "number": "AUD-2023-100"
   },
   "auditItemId": "d106e5f4-e708-7190-2a1b-4c5d6e7f8091",
   "auditObject": {
      "id": "e207f605-f809-8a0b-3c2d-5e6f70819203",
      "name": "Building A - First Floor"
   },
   "createdAtUtc": "2023-10-31T11:05:37.688Z",
   "createdBy": {
      "id": "f3080706-09a0-9b1c-4d3e-607182930415",
      "name": "John Smith"
   },
   "description": "Replace missing fire extinguisher in hallway near conference room 101",
   "dueDateUtc": "2023-11-01T06:59:59.000Z",
   "expiredAtUtc": "2023-11-03T06:59:59.000Z",
   "expiredBy": {
      "id": "a4b908c7-d0e1-0120-5a4b-7c8d9e0f1a2b",
      "name": "Lisa Chen"
   },
   "id": "a5b0c9d8-e1f2-13a4-6b5c-8d9e0f1a2b3c",
   "information": {
      "text": "Fire extinguisher has been ordered and will be installed by facilities team",
      "photosIds": [
         "a6b1c0d9-e2f3-2a4b-7c6d-9e0f1a2b3c4d"
      ],
      "files": [
         {
            "id": "a7b2c1d0-e3f4-3a5b-8c7d-0e1f2a3b4c5d",
            "name": "fire_extinguisher_order_receipt.pdf",
            "contentType": "application/pdf",
            "updatedAt": "2023-11-02T09:15:33.456Z"
         }
      ]
   },
   "name": "Fire Extinguisher Replacement",
   "number": "CA-2023-001",
   "priority": 2,
   "question": "Is the fire extinguisher present and accessible?",
   "status": 3,
   "tags": [
      {
         "id": "a8b3c2d1-e4f5-4a6b-9c8d-1e2f3a4b5c6d",
         "name": "Fire Safety"
      }
   ],
   "files": [
      {
         "id": "a9b4c3d2-e5f6-5a7b-0c9d-2e3f4a5b6c7d",
         "name": "corrective_action_photos.jpg",
         "contentType": "image/jpeg",
         "updatedAt": "2023-10-31T11:05:37.688Z"
      }
   ],
   "issue": {
      "id": "b0c5d4e3-f6a7-6b8c-1d0e-3f4a5b6c7d8e",
      "name": "Missing fire extinguisher",
      "isDeleted": false
   },
   "metafields": []
}
```

### Response fields

| Field | Type | Description |
|-------|------|-------------|
| `id` | uuid | Corrective action identifier |
| `answer` | object | Optional. Answer summary: `name`, `points`, `text`, `number`, `isFailed` |
| `approvedAtUtc` | string (UTC) | Optional. When approved |
| `approvedBy` | object | Optional. `id`, `name` |
| `assignedUsers` | array | Assignees; each `id`, `name` |
| `audit` | object | Optional. `id`, `name`, `ianaTimeZone`, `number` |
| `auditItemId` | uuid | Optional. Related audit item |
| `auditObject` | object | `id`, `name` |
| `createdAtUtc` | string (UTC) | Created at |
| `createdBy` | object | `id`, `name` |
| `description` | string | Description |
| `dueDateUtc` | string (UTC) | Due date |
| `expiredAtUtc` | string (UTC) | Optional. When expired |
| `expiredBy` | object | Optional. `id`, `name` |
| `information` | object | Optional. `text`, `photosIds` (array of uuid), `files` (same shape as top-level `files`) |
| `name` | string | Title |
| `number` | string | Reference number |
| `priority` | integer | Priority: `0` (Low), `1` (Medium), `2` (High) |
| `question` | string | Related question text |
| `status` | integer | Status: `0` (Open), `1` (Approved), `2` (Rejected), `3` (Submitted), `4` (Expired) |
| `tags` | array | Each item `id` (uuid), `name` (string) |
| `files` | array | File metadata: `id`, `name`, `contentType`, `updatedAt` |
| `issue` | object | Optional. `id`, `name`, `isDeleted` |
| `metafields` | array | Metafield objects (`id`, `name`, `answerType`, `data` per item) |

For error responses, see the [response status codes documentation](#/response-status-codes).
