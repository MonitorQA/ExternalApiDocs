---
category: 5. Audit Objects
url_path: '/audit/objects'
title: 'Delete audit objects'
type: 'DELETE'
order: 5
layout: null
---

This method allows you to delete multiple audit objects in a single request.

### Request Headers

| Header | Type | Required | Description |
|--------|------|----------|-------------|
| `X-API-KEY` | string | Yes | Your API authentication key |
| `Content-Type` | string | Yes | Must be `application/json` |

### Request Body Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `ids` | array[string] | Yes | Array of audit object IDs to delete |

### Example Request

```http
DELETE /audit/objects
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

For errors responses, see the [response status codes documentation](#/response-status-codes).
