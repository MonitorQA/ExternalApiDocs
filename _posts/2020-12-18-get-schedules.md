---
category: Schedules
categoryOrder: 3
url_path: '/schedules'
title: 'Get schedules list'
type: 'GET'
order: 1
layout: null
---

Retrieve a paginated list of active audit schedules with optional filtering. Query parameter `auditObjectUnitId` is a **company structure unit** ID; results include schedules that target **audit objects linked to that unit**. See [Get company structure units](#/get-company-structure-units). The legacy name `auditObjectGroupId` is still accepted with the same meaning.

### Request Headers

| Header | Type | Required | Description |
|--------|------|----------|-------------|
| `X-API-KEY` | string | Yes | API authentication key |

### Query Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `auditObjectId` | uuid | No | Filter schedules by specific audit object ID |
| `auditObjectUnitId` | uuid | No | Company structure unit ID. Filter schedules that include **audit objects linked to that unit** |
| `pageNumber` | integer | No | Page number for pagination, starting from 1 (default: 1) |
| `pageSize` | integer | No | Number of items per page (default: 10) |

### Example Request

```http
GET /schedules?pageNumber=1&pageSize=20
Host: api-external.monitorqa.com
X-API-KEY: abcdef12345
```

## Response

**Success Response**

See [schedule details](#/get-schedule) for details about **`repeatPattern`** and **`repeat`** options. Each list item includes **`auditObjectUnits`**: company structure units whose linked audit objects are included on the schedule (`id`, `name` on each entry).

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "data": [
     {
         "id": "123e4567-e89b-12d3-a456-426614174000",
         "name": "Daily Safety Inspections",
         "repeatPattern": 1,
         "active": true,
         "stopByDate": "2025-12-31T23:59:59.000Z",
         "startFromDate": "2025-01-01T00:00:00.000Z",
         "template": {
            "id": "456e7890-e89b-12d3-a456-426614174001",
            "name": "Kitchen Safety Template"
         },
         "repeat": {
            "repeatEvery": 3
         },
         "auditObjects": [{
            "id": "789e0123-e89b-12d3-a456-426614174002",
            "name": "Main Kitchen"
         }],
         "auditObjectUnits": [{
            "id": "abc12345-e89b-12d3-a456-426614174003",
            "name": "Operations"
         }]
      }
  ],
  "meta": {
    "pageNumber": 1,
    "pageSize": 10,
    "totalCount": 1
  }
}
```

For error responses, see the [response status codes documentation](#/response-status-codes).
