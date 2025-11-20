---
category: 11. Score systems
categoryOrder: 11
url_path: '/score-systems/{id}'
title: 'Update score system'
type: 'PUT'
order: 4
layout: null
---

Update an existing score system with new configuration, labels, and settings.

### Request Headers

| Header | Type | Required | Description |
|--------|------|----------|-------------|
| `X-API-KEY` | string | Yes | API authentication key |
| `Content-Type` | string | Yes | Must be `application/json` |

### Path Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `id` | uuid | Yes | Unique identifier of the score system |

### Request Body Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `name` | string | Yes | Score system name |
| `description` | string | No | Description of the score system |
| `passedThreshold` | number | Yes | Threshold value for passing |
| `scoreSystemType` | number | No | Score system type: `0` (ProportionToMaxScorePoints) or `1` (CountNotApplicableAsPositive) |
| `labels` | array | Yes | Array of score labels (at least one required) |
| `labels[].min` | number | Yes | Minimum score value for this label |
| `labels[].max` | number | Yes | Maximum score value for this label (must be >= min) |
| `labels[].label` | string | Yes | Label text |
| `labels[].color` | string | Yes | Color code for this label |

### Score System Types

| Value | Description |
|-------|-------------|
| `0` | ProportionToMaxScorePoints - Calculates score as proportion of maximum possible points |
| `1` | CountNotApplicableAsPositive - Counts not applicable items as positive in score calculation |

### Example Request

```http
PUT /score-systems/123e4567-e89b-12d3-a456-426614174000
Host: api-external.monitorqa.com
X-API-KEY: abcdef12345
Content-Type: application/json

{
  "name": "Updated Scoring System",
  "description": "Updated description",
  "passedThreshold": 75,
  "scoreSystemType": 1,
  "labels": [
    {
      "min": 0,
      "max": 60,
      "label": "Fail",
      "color": "#FF0000"
    },
    {
      "min": 61,
      "max": 100,
      "label": "Pass",
      "color": "#00FF00"
    }
  ]
}
```

## Response

**Success Response**

```http
HTTP/1.1 200 OK
```

Empty response body indicates successful update.

For errors responses, see the [response status codes documentation](#/response-status-codes).

