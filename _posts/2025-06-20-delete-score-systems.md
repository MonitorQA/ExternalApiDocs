---
category: Score systems
categoryOrder: 11
url_path: '/score-systems'
title: 'Delete score systems'
type: 'DELETE'
order: 5
layout: null
---

Delete one or more score systems. Score systems that are associated with templates cannot be deleted and will return an error.

### Request Headers

| Header | Type | Required | Description |
|--------|------|----------|-------------|
| `X-API-KEY` | string | Yes | API authentication key |
| `Content-Type` | string | Yes | Must be `application/json` |

### Request Body Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `ids` | array[uuid] | Yes | Array of score system IDs to delete |

### Example Request

```http
DELETE /score-systems
Host: api-external.monitorqa.com
X-API-KEY: abcdef12345
Content-Type: application/json

{
  "ids": [
    "123e4567-e89b-12d3-a456-426614174000",
    "987f6543-a21b-43c5-d654-321987654321"
  ]
}
```

## Response

**Success Response**

```http
HTTP/1.1 200 OK
```

Empty response body indicates successful deletion.

**Error Response (Score System Has Templates)**

```http
HTTP/1.1 409 Conflict
Content-Type: application/json

{
  "message": "score-system/has-templates:123e4567-e89b-12d3-a456-426614174000"
}
```

If a score system is associated with templates, it cannot be deleted and the error response will include the IDs of score systems that have templates.

For errors responses, see the [response status codes documentation](#/response-status-codes).

