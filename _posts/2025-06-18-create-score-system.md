---
category: Score systems
categoryOrder: 11
url_path: '/score-systems'
title: 'Create score system'
type: 'POST'
order: 3
layout: null
---

Create a new score system with labels and configuration. Score systems define how audit scores are calculated and displayed.

### Request Headers

| Header | Type | Required | Description |
|--------|------|----------|-------------|
| `X-API-KEY` | string | Yes | API authentication key |
| `Content-Type` | string | Yes | Must be `application/json` |

### Request Body Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `name` | string | Yes | Score system name |
| `description` | string | No | Description of the score system |
| `passedThreshold` | number | Yes | Threshold value for passing |
| `scoreSystemType` | number | Yes | Score system type: `0` (ProportionToMaxScorePoints) or `1` (CountNotApplicableAsPositive). Cannot be changed after creation |
| `labels` | array | Yes | Array of score labels (at least one required) |
| `labels[].min` | number | Yes | Minimum score value for this label |
| `labels[].max` | number | Yes | Maximum score value for this label (must be >= min) |
| `labels[].label` | string | Yes | Label text |
| `labels[].color` | string | Yes | Color code for this label |

### Label Validation Rules

Labels must meet the following requirements:

- **Full Range Coverage**: Labels must cover the entire interval from 0 to 100
  - The first label must start at 0 (`min: 0`)
  - The last label must end at 100 (`max: 100`)
- **No Overlaps**: Label ranges cannot overlap (e.g., `[0-50]` and `[40-80]` is invalid)
- **No Gaps**: Label ranges must be continuous with no gaps. The next label's `min` must equal the previous label's `max` (e.g., `[0-50]` and `[60-100]` is invalid; should be `[0-50]` and `[50-100]`)

**Valid Example**: `[{min: 0, max: 50}, {min: 50, max: 80}, {min: 80, max: 100}]` ✓

**Invalid Examples**:
- `[{min: 10, max: 50}, {min: 50, max: 100}]` ✗ (doesn't start at 0)
- `[{min: 0, max: 50}, {min: 50, max: 90}]` ✗ (doesn't end at 100)
- `[{min: 0, max: 50}, {min: 40, max: 100}]` ✗ (overlap - 40 < 50)
- `[{min: 0, max: 50}, {min: 60, max: 100}]` ✗ (gap - next min (60) should equal previous max (50))

### Score System Types

| Value | Description |
|-------|-------------|
| `0` | ProportionToMaxScorePoints - Calculates score as proportion of maximum possible points |
| `1` | CountNotApplicableAsPositive - Counts not applicable items as positive in score calculation |

### Example Request

```http
POST /score-systems
Host: api-external.monitorqa.com
X-API-KEY: abcdef12345
Content-Type: application/json

{
  "name": "Standard Scoring",
  "description": "Standard scoring system for audits",
  "passedThreshold": 70,
  "scoreSystemType": 0,
  "labels": [
    {
      "min": 0,
      "max": 50,
      "label": "Poor",
      "color": "#FF0000"
    },
    {
      "min": 50,
      "max": 80,
      "label": "Good",
      "color": "#FFFF00"
    },
    {
      "min": 80,
      "max": 100,
      "label": "Excellent",
      "color": "#00FF00"
    }
  ]
}
```

## Response

**Success Response**

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "id": "123e4567-e89b-12d3-a456-426614174000"
}
```

### Response Fields

| Field | Type | Description |
|-------|------|-------------|
| `id` | uuid | Unique identifier of the created score system |

For errors responses, see the [response status codes documentation](#/response-status-codes).

