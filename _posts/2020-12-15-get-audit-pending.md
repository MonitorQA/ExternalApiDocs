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
| `fromDate` | string | No | Filter by audit due date (UTC format: `yyyy-MM-ddTHH:mm:ss.fffZ`) |
| `toDate` | string | No | Filter by audit due date (UTC format: `yyyy-MM-ddTHH:mm:ss.fffZ`) |
| `pageNumber` | number | No | Current page number, starts from 1 |
| `pageSize` | number | No | Page size |
| `orderBy` | string | No | Field to sort by (default: 'name') |
| `orderByDirection` | string | No | Sort direction (`asc` or `desc`) |

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

### Response

**If succeeds**, returns a list of audit details.

```Status: 200 OK```

```{
  "data": [
    {
      "id": "string",
      "name": "string",
      "assignees": [
        {
          "id": "string",
          "name": "string"
        }
      ],
      "auditObject": {
        "id": "string",
        "name": "string"
      },
      "endDate": "2021-12-30T13:46:13.413Z",
      "number": "string",
      "startDate": "2021-12-30T13:46:13.413Z",
      "template": {
        "id": "string",
        "name": "string"
      },
      "isReopened": true,
      "isStarted": true,
      "completedActionsCount": 0,
      "pendingActionsCount": 0
    }
  ],
  "meta": {
    "pageNumber": 0,
    "pageSize": 0,
    "totalCount": 0
  }
}```

For errors responses, see the [response status codes documentation](#/response-status-codes).
