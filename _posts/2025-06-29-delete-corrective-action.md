---
category: Corrective Actions
categoryOrder: 10
url_path: '/corrective-actions/{id}'
title: 'Delete corrective action'
type: 'DELETE'
order: 6
layout: null
---

Delete a specific corrective action by its unique identifier. This endpoint permanently removes the corrective action from the system.

### Request Headers

| Header | Type | Required | Description |
|--------|------|----------|-------------|
| `X-API-KEY` | string | Yes | API authentication key |

### Path Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `id` | uuid | Yes | The unique identifier of the corrective action to delete |

### Example Request

```http
DELETE /corrective-actions/123e4567-e89b-12d3-a456-426614174000
Host: api-external.monitorqa.com
X-API-KEY: abcdef12345
```

## Response

**Success Response**

```http
HTTP/1.1 200 OK
```

Empty response body indicates successful deletion of the corrective action.

For errors responses, see the [response status codes documentation](#/response-status-codes).

