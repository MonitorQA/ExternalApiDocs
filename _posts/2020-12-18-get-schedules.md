---
category: 3. Schedules
categoryOrder: 3
url_path: '/schedules'
title: 'Get schedules list'
type: 'GET'
order: 1
layout: null
---

Retrieve a paginated list of active audit schedules with optional filtering and sorting capabilities.

### Request Headers

| Header | Type | Required | Description |
|--------|------|----------|-------------|
| `X-API-KEY` | string | Yes | API authentication key |

### Query Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `auditObjectId` | string | No | Filter schedules by specific audit object ID |
| `auditObjectGroupId` | string | No | Filter schedules by audit object group ID |
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

See [schedule details](#/get-schedule) for details about **`repeatPattern`** and **`repeat`** options

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "data": [
     {
         "id": string,
         "name": string,
         "repeatPattern": 1,
         "active": boolean,
         "stopByDate": "2025-12-31T23:59:59.000Z",
         "startFromDate": "2025-01-01T00:00:00.000Z",
         "template": {
            "id": string,
            "name": string
         },
         "repeat": {
            "repeatEvery": 3
         },
         "auditObjects: [{
            "id": string,
            "name": string
         }],
         "auditObjectGroups": [{
            "id": string,
            "name": string
         }]
      }
  ],
  "meta": {
    "pageNumber": 0,
    "pageSize": 10,
    "totalCount": 1
  }
}
```

For errors responses, see the [response status codes documentation](#/response-status-codes).
