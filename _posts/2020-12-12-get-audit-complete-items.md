---
category: Audits
categoryOrder: 2
url_path: '/audit/complete/{auditId}/report'
title: 'Get audit report'
type: 'GET'
order: 2
layout: null
---

Retrieve the detailed report of a completed audit, including all audit items, their statuses, and associated corrective actions.

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
GET /audit/complete/{auditId}/report
Host: api-external.monitorqa.com
X-API-KEY: abcdef12345
```

## Response

**Success Response**

Root object: `id` (string, audit id in UUID format), `items` (array of report items).

Each **item** includes:

| Field | Type | Description |
|-------|------|-------------|
| `id` | uuid | Audit item id |
| `text` | string | Item text |
| `note` | string | Auditor note |
| `notApplicable` | boolean | N/A flag |
| `isCritical` | boolean | Critical flag |
| `isPassed` | boolean | Optional. Pass/fail where applicable |
| `isFailed` | boolean | Failed flag |
| `childrenIds` | array[uuid] | Child item ids |
| `actions` | array | Corrective actions (see below) |
| `photos` | array | Item photos |
| `itemsCount` | integer | Optional. Child item count |
| `points` | object | Optional. `total`, `selected`, `score`, `previousScore`, `color` |
| `signature` | object | Optional. `photoId` (uuid), `createdBy` (`id`, `name`) |
| `failedInRowCount` | integer | Consecutive failures count |
| `itemType` | integer | Item type (see table below) |
| `data` | object | Answer summary: `name`, `points`, `text`, `number`, `isFailed` |
| `metafields` | array | Each: `name`, `text` |

Each element of **`actions`** (corrective action summary):

| Field | Type | Description |
|-------|------|-------------|
| `id` | uuid | Corrective action id |
| `name` | string | Name |
| `number` | string | Number |
| `description` | string | Description |
| `assignedUsers` | array | Assignees; each `id` (uuid), `name` (string) |
| `createdBy` | object | `id` (uuid), `name` (string) |
| `createdAt` | string (UTC) | Optional. Created at |
| `dueDate` | string (UTC) | Optional. Due date |
| `priority` | integer | Priority (see below) |
| `status` | integer | Status (see below) |
| `photos` | array | Photo metadata |
| `files` | array | File references |
| `tags` | array | Tag objects |
| `metafields` | array | Metafield objects |

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
   "id": "1acad6ca-cab8-48a7-07f2-08da929c74ab",
   "items": [
      {
         "id": "4ff6fbf7-8e6d-46be-356c-08da929d03c7",
         "text": "Fire extinguisher present and accessible",
         "note": "Located near main entrance - needs pressure check",
         "notApplicable": false,
         "isCritical": true,
         "isPassed": false,
         "isFailed": false,
         "childrenIds": [],
         "metafields": [{
            "name": "Metafield name",
            "text": "Metafield user input"
         }],
         "actions": [
            {
               "id": "a1b2c3d4-e5f6-789a-bcde-f01234567890",
               "name": "Schedule fire extinguisher maintenance",
               "number": "CA-2023-0892",
               "description": "Contact certified technician for monthly pressure check",
               "assignedUsers": [
                    {
                        "id": "b2c3d4e5-f6a7-890b-cdef-012345678901",
                        "name": "David Martinez"
                    }
                ],
               "createdBy": {
                  "id": "3c71b2a5-4c00-4bb0-9f08-785a2d8f7128",
                  "name": "Jennifer Thompson"
               },
               "createdAt": "2023-09-12T03:10:30.133Z",
               "dueDate": "2023-09-27T23:59:59.999Z",
               "priority": 2,
               "status": 0,
               "photos": [],
               "files": [],
               "tags": [],
               "metafields": []
            }
         ],
         "photos": [],
         "itemsCount": null,
         "points": null,
         "signature": {
            "photoId": "a49d853b-c51b-488d-adc9-3baeab3bde3e",
            "createdBy": {
               "id": "3c71b2a5-4c00-4bb0-9f08-785a2d8f7128",
               "name": "Jennifer Thompson"
            }
         },
         "failedInRowCount": 1,
         "itemType": 2,
         "data": {
            "name": null,
            "points": 0.0000,
            "text": null,
            "number": 4.0000,
            "isFailed": true
         }
      }
   ]
}
```

### itemType values

| Value | Description |
|-------|-------------|
| `0` | Root |
| `1` | Section |
| `2` | Item |
| `3` | ConditionalItem |
| `4` | Condition |

### actions.priority values

| Value | Description |
|-------|-------------|
| `0` | Low |
| `1` | Medium |
| `2` | High |

### actions.status values

| Value | Description |
|-------|-------------|
| `0` | Open |
| `1` | Approved |
| `2` | Rejected |
| `3` | Submitted |

For errors responses, see the [response status codes documentation](#/response-status-codes).

