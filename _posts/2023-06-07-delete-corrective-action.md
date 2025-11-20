---
category: 10. Corrective Actions
categoryOrder: 10
url_path: '/corrective-actions/{id}'
title: 'Delete corrective action'
type: 'DELETE'
order: 9
layout: null
---

Delete a specific corrective action from your organization. Use this endpoint to permanently remove corrective actions that are no longer needed. This action cannot be undone.

## Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| id | string | Yes | The unique identifier of the corrective action to delete |

### Example Request

```http
DELETE /corrective-actions/{id}
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
