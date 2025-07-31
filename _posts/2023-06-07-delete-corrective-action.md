---
category: 9. Corrective Actions
url_path: '/corrective-actions/{id}'
title: 'Delete corrective action'
type: 'DELETE'
order: 6
layout: null
---

Delete a specific corrective action from your organization. Use this endpoint to permanently remove corrective actions that are no longer needed. This action cannot be undone.

## Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| id | string | Yes | The unique identifier of the corrective action to delete |

## Request Example

```http
DELETE https://api-external.monitorqa.com/corrective-actions/{id}
X-API-KEY: abcdef12345
```

## Response

**Success Response**

```http
HTTP/1.1 200 OK
```

Empty response body indicates successful deletion of the corrective action.


For errors responses, see the [response status codes documentation](#/response-status-codes).
