---
category: Webhook
categoryOrder: 13
url_path: '/webhooks'
title: 'Set webhook'
type: 'POST'
order: 2
layout: null
---

Set or update the webhook URL for your company. This endpoint allows you to configure where MonitorQA will send webhook notifications for audit and corrective action events. The webhook URL must be a valid absolute URL and cannot be a loopback address or point to monitorqa.com domains.

**Note:** For information about webhook events and message formats, see the [Webhook documentation](#/webhook).

### Request Headers

| Header | Type | Required | Description |
|--------|------|----------|-------------|
| `X-API-KEY` | string | Yes | API authentication key |
| `Content-Type` | string | Yes | Must be `application/json` |

### Request Body Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `url` | string | Yes | The webhook URL where MonitorQA will send notifications. Must be a valid absolute URL (e.g., `https://your-domain.com/webhook`). Cannot be a loopback address or point to monitorqa.com domains |

### URL Validation Rules

The webhook URL must meet the following requirements:
- Must be an absolute URL (e.g., `https://example.com/webhook`)
- Cannot be a loopback address (e.g., `http://localhost`, `http://127.0.0.1`)
- Cannot point to monitorqa.com domains
- Must use a valid URL scheme (http or https)

### Example Request

```http
POST /webhooks
Host: api-external.monitorqa.com
X-API-KEY: abcdef12345
Content-Type: application/json

{
  "url": "https://your-webhook-endpoint.com/notifications"
}
```

## Response

**Success Response**

```http
HTTP/1.1 200 OK
```

Empty response body indicates successful webhook configuration.

**Error Responses**

The API will return `409 Conflict` with error code `validation/webhook-url-not-valid` if the provided URL does not meet the validation requirements.

For other error responses, see the [response status codes documentation](#/response-status-codes).
