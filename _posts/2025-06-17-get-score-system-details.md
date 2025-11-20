---
category: 11. Score systems
categoryOrder: 11
url_path: '/score-systems/{id}'
title: 'Get score system details'
type: 'GET'
order: 2
layout: null
---

Retrieve detailed information about a specific score system including all its labels and configuration.

### Request Headers

| Header | Type | Required | Description |
|--------|------|----------|-------------|
| `X-API-KEY` | string | Yes | API authentication key |

### Path Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `id` | uuid | Yes | Unique identifier of the score system |

### Example Request

```http
GET /score-systems/123e4567-e89b-12d3-a456-426614174000
Host: api-external.monitorqa.com
X-API-KEY: abcdef12345
```

## Response

**Success Response**

```http
HTTP/1.1 200 OK
Content-Type: application/json

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
```

### Response Fields

| Field | Type | Description |
|-------|------|-------------|
| `id` | uuid | Unique identifier of the score system |
| `name` | string | Score system name |
| `description` | string | Optional description of the score system |
| `passedThreshold` | number | Optional threshold value for passing |
| `scoreSystemType` | number | Score system type: `0` (ProportionToMaxScorePoints) or `1` (CountNotApplicableAsPositive) |
| `isSample` | boolean | Whether this is a sample score system |
| `labels` | array | Array of score labels |
| `labels[].id` | uuid | Unique identifier of the label |
| `labels[].label` | string | Label text |
| `labels[].min` | number | Minimum score value for this label |
| `labels[].max` | number | Maximum score value for this label |
| `labels[].color` | string | Color code for this label |

For errors responses, see the [response status codes documentation](#/response-status-codes).

