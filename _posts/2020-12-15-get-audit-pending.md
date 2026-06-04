---
category: Audits
categoryOrder: 2
url_path: '/audit/pending'
title: 'Get list of pending audits'
type: 'GET'
order: 2
layout: null
---

Retrieve a paginated list of pending audits with filtering and sorting options. `auditObjectUnitId` is a **company structure unit** identifier: it limits results to audits whose audit object is linked to that unit. `assignedToUnit` limits results to audits assigned to **users linked to that unit**. Use [Get company structure units](#/get-company-structure-units) to list valid unit IDs. The legacy query name `auditObjectGroupId` is still accepted and means the same filter.

### Request Headers

| Header | Type | Required | Description |
|--------|------|----------|-------------|
| `X-API-KEY` | string | Yes | API authentication key |

### Query Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `inProgress` | boolean | No | Filter by in progress state |
| `templateId` | uuid | No | Filter by audit template ID |
| `auditObjectId` | uuid | No | Filter by audit object ID |
| `auditObjectUnitId` | uuid | No | Company structure unit ID. Matches audits whose audit object is linked to that unit |
| `auditScheduleId` | uuid | No | Filter by audit schedule ID |
| `assignedTo` | uuid | No | Filter by assigned user ID |
| `assignedToUnit` | uuid | No | Filter by company structure unit ID. Matches audits assigned to **users linked to that unit** |
| `pageNumber` | number | No | Current page number, starts from 1 |
| `pageSize` | number | No | Page size |

**Note:** This method will return an empty data list if the requested page does not exist.

### Example Request

```http
GET /audit/pending?inProgress=true&auditScheduleId=d4e5f6a7-b8c9-7012-def4-567890123gbc&pageSize=50
Host: api-external.monitorqa.com
X-API-KEY: abcdef12345
```

## Response

**Success Response**

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "data": [
    {
      "id": "a1b2c3d4-e5f6-4789-abc1-234567890def",
      "name": "Weekly Kitchen Safety Inspection",
      "assignees": [
        {
          "id": "b2c3d4e5-f6a7-5890-bcd2-345678901efa",
          "name": "Emily Davis"
        }
      ],
      "auditObject": {
        "id": "c3d4e5f6-a7b8-6901-cde3-456789012fab",
        "name": "Main Kitchen - Building B"
      },
      "endDate": "2023-12-15T17:00:00.000Z",
      "number": null,
      "startDate": "2023-12-15T09:00:00.000Z",
      "template": {
        "id": "d4e5f6a7-b8c9-7012-def4-567890123gbc",
        "name": "Kitchen Safety Inspection Template"
      },
      "isStarted": true
    },
    {
      "id": "e5f6a7b8-c9d0-8123-efg5-678901234hcd",
      "name": "Monthly Equipment Maintenance Check",
      "assignees": [
        {
          "id": "f6a7b8c9-d0e1-9234-fgh6-789012345ide",
          "name": "Robert Wilson"
        },
        {
          "id": "a7b8c9d0-e1f2-0345-ghi7-890123456jef",
          "name": "Maria Garcia"
        }
      ],
      "auditObject": {
        "id": "b8c9d0e1-f2a3-1456-hij8-901234567kfg",
        "name": "Manufacturing Floor - Zone A"
      },
      "endDate": "2023-12-20T16:30:00.000Z",
      "number": null,
      "startDate": "2023-12-18T08:00:00.000Z",
      "template": {
        "id": "c9d0e1f2-a3b4-2567-ijk9-012345678lgh",
        "name": "Equipment Maintenance Audit"
      },
      "isStarted": true
    }
  ],
  "meta": {
    "pageNumber": 1,
    "pageSize": 50,
    "totalCount": 2
  }
}
```

Each element of `data` has: `id` (uuid), `name` (string), `assignees` (array of `id`, `name`), `auditObject` (`id`, `name`), `endDate` (string UTC or null), `number` (string or null), `startDate` (string UTC or null), `template` (`id`, `name`), `isStarted` (boolean).

For errors responses, see the [response status codes documentation](#/response-status-codes).
