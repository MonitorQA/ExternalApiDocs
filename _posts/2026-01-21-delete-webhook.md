---
category: Webhook
categoryOrder: 13
url_path: '/webhooks'
title: 'Delete webhook'
type: 'DELETE'
order: 3
layout: null
---

Delete the webhook configuration for your company. This endpoint removes the webhook URL. After deletion, MonitorQA will no longer send webhook notifications for your company.

### Request Headers

| Header | Type | Required | Description |
|--------|------|----------|-------------|
| `X-API-KEY` | string | Yes | API authentication key |

### Example Request

```http
DELETE /webhooks
Host: api-external.monitorqa.com
X-API-KEY: abcdef12345
```

## Response

**Success Response**

```http
HTTP/1.1 200 OK
```

Empty response body indicates successful webhook deletion.

For errors responses, see the [response status codes documentation](#/response-status-codes).
