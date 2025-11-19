---
category: 10. Score systems
url_path: '/score-systems'
title: 'Get score systems'
type: 'GET'
order: 1
layout: null
---

Retrieve a paginated list of score systems for the company. Score systems define how audit scores are calculated and displayed with labels and color coding.

### Request Headers

| Header | Type | Required | Description |
|--------|------|----------|-------------|
| `X-API-KEY` | string | Yes | API authentication key |

### Query Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `pageNumber` | number | No | Page number (default: 1) |
| `pageSize` | number | No | Number of items per page (default: 10) |
| `search` | string | No | Search term to filter score systems by name |

### Example Request

```http
GET /score-systems?pageNumber=1&pageSize=10
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
      "id": "123e4567-e89b-12d3-a456-426614174000",
      "name": "Standard Scoring",
      "description": "Standard scoring system for audits",
      "passedThreshold": 70,
      "scoreSystemType": 0,
      "isSample": false,
      "labels": [
        {
          "id": "789e4567-e89b-12d3-a456-426614174001",
          "label": "Poor",
          "min": 0,
          "max": 50,
          "color": "#FF0000"
        },
        {
          "id": "789e4567-e89b-12d3-a456-426614174002",
          "label": "Good",
          "min": 51,
          "max": 80,
          "color": "#FFFF00"
        },
        {
          "id": "789e4567-e89b-12d3-a456-426614174003",
          "label": "Excellent",
          "min": 81,
          "max": 100,
          "color": "#00FF00"
        }
      ]
    }
  ],
  "meta": {
    "pageSize": 10,
    "pageNumber": 1,
    "totalCount": 1
  }
}
```

### Response Fields

| Field | Type | Description |
|-------|------|-------------|
| `data` | array | Array of score system objects |
| `data[].id` | uuid | Unique identifier of the score system |
| `data[].name` | string | Score system name |
| `data[].description` | string | Optional description of the score system |
| `data[].passedThreshold` | number | Optional threshold value for passing |
| `data[].scoreSystemType` | number | Score system type: `0` (ProportionToMaxScorePoints) or `1` (CountNotApplicableAsPositive) |
| `data[].isSample` | boolean | Whether this is a sample score system |
| `data[].labels` | array | Array of score labels |
| `data[].labels[].id` | uuid | Unique identifier of the label |
| `data[].labels[].label` | string | Label text |
| `data[].labels[].min` | number | Minimum score value for this label |
| `data[].labels[].max` | number | Maximum score value for this label |
| `data[].labels[].color` | string | Color code for this label |
| `meta` | object | Pagination metadata |
| `meta.pageSize` | number | Number of items per page |
| `meta.pageNumber` | number | Current page number |
| `meta.totalCount` | number | Total number of items available |

For errors responses, see the [response status codes documentation](#/response-status-codes).

