---
category: 2. Audits
url_path: '/audit/pending'
title: 'Get list of pending audits'
type: 'GET'
order: 6
layout: null
---

This method allows you to retrieve a paginated list of pending audits with filtering and sorting options.

### Request Headers

| Header | Type | Required | Description |
|--------|------|----------|-------------|
| `X-API-KEY` | string | Yes | Your API authentication key |

### Query Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `inProgress` | boolean | No | Filter by in progress state |
| `templateId` | string | No | Filter by audit template ID |
| `auditObjectId` | string | No | Filter by audit object ID |
| `auditObjectGroupId` | string | No | Filter by audit object group ID |
| `assignedTo` | string | No | Filter by assigned user ID |
| `assignedToGroup` | string | No | Filter by assigned user group ID |
| `pageNumber` | number | No | Current page number, starts from 1 |
| `pageSize` | number | No | Page size |
| `orderBy` | string | No | Field to sort by (default: 'name') |
| `orderByDirection` | string | No | Sort direction (`asc` or `desc`) |

**Note:** This method will return an empty data list if the requested page does not exist.

### Sorting Options

**orderBy** values:

| Value | Description |
|-------|-------------|
| `name` | Sort by audit name |
| `auditObjectName` | Sort by audit object name |
| `endDate` | Sort by audit end date |
| `assignedTo` | Sort by assigned user name |

**orderByDirection** values:

| Value | Description |
|-------|-------------|
| `asc` | Ascending order |
| `desc` | Descending order |

### Example Request

```http
GET /audit/pending?inProgress=true&pageSize=50&orderBy=endDate&orderByDirection=asc
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
      "number": "AUD-2023-1247",
      "startDate": "2023-12-15T09:00:00.000Z",
      "template": {
        "id": "d4e5f6a7-b8c9-7012-def4-567890123gbc",
        "name": "Kitchen Safety Inspection Template"
      },
      "isReopened": false,
      "isStarted": true,
      "completedActionsCount": 8,
      "pendingActionsCount": 3
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
      "number": "AUD-2023-1248",
      "startDate": "2023-12-18T08:00:00.000Z",
      "template": {
        "id": "c9d0e1f2-a3b4-2567-ijk9-012345678lgh",
        "name": "Equipment Maintenance Audit"
      },
      "isReopened": true,
      "isStarted": true,
      "completedActionsCount": 15,
      "pendingActionsCount": 7
    }
  ],
  "meta": {
    "pageNumber": 1,
    "pageSize": 50
  }
}
```

For errors responses, see the [response status codes documentation](#/response-status-codes).
