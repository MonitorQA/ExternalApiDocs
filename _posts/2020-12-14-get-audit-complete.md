---
category: 2. Audits
url_path: '/audit/complete'
title: 'Get list of complete audits'
type: 'GET'
order: 8
layout: null
---

This method allows you to retrieve a paginated list of completed audits with advanced filtering and sorting options.

### Request Headers

| Header | Type | Required | Description |
|--------|------|----------|-------------|
| `X-API-KEY` | string | Yes | Your API authentication key |

### Query Parameters
| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `scoreMin` | number | No | Filter by minimum score |
| `scoreMax` | number | No | Filter by maximum score |
| `completedBy` | string | No | Filter by user ID who completed audit |
| `completedByGroup` | string | No | Filter by user group ID |
| `templateId` | string | No | Filter by audit template ID |
| `auditObjectId` | string | No | Filter by audit object ID |
| `auditObjectGroupId` | string | No | Filter by audit object group ID |
| `assignedTo` | string | No | Filter by assigned user ID |
| `assignedToGroup` | string | No | Filter by assigned user group ID |
| `fromDate` | string | No | Filter by audit completion date (UTC format: `yyyy-MM-ddTHH:mm:ss.fffZ`) |
| `toDate` | string | No | Filter by audit completion date (UTC format: `yyyy-MM-ddTHH:mm:ss.fffZ`) |
| `pageNumber` | number | No | Current page number, starts from 1 (default: 1) |
| `pageSize` | number | No | Page size (default: 100) |
| `orderBy` | string | No | Field to sort by (default: 'name') |
| `orderByDirection` | string | No | Sort direction (`asc` or `desc`) |

### Sorting Options

**orderBy** values:

| Value | Description |
|-------|-------------|
| `number` | Sort by audit number |
| `auditObjectName` | Sort by audit object name |
| `score` | Sort by score value |
| `completeDate` | Sort by audit completion date |
| `completedBy` | Sort by completed by user name |

**orderByDirection** values:

| Value | Description |
|-------|-------------|
| `asc` | Ascending order |
| `desc` | Descending order |

### Example Request

```http
GET /audit/complete?scoreMin=80&pageSize=50&orderBy=completeDate&orderByDirection=desc
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
      "endDate": "2021-12-30T13:57:38.999Z",
      "number": "string",
      "startDate": "2021-12-30T13:57:38.999Z",
      "template": {
        "id": "string",
        "name": "string"
      },
      "completeDate": "2021-12-30T13:57:38.999Z",
      "completedBy": {
        "id": "string",
        "name": "string"
      },
      "score": 0,
      "scoreLabel": "string"
    }
  ],
  "meta": {
    "pageNumber": 0,
    "pageSize": 0,
    "totalCount": 0
  }
}```

For errors responses, see the [response status codes documentation](#/response-status-codes).
