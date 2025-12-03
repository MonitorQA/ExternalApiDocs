---
category: Webhook Log
categoryOrder: 13
url_path: '/webhooks/status'
title: 'Get webhooks log'
type: 'GET'
order: 1
layout: null
---

Retrieve a paginated history of executed webhooks, including their status, response codes, and any error messages. This endpoint helps monitor webhook delivery and troubleshoot integration issues.

## Query Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| pageNumber | integer | No | Page number for pagination (starts from 1) |
| pageSize | integer | No | Number of items per page |

### Example Request

```http
GET /webhooks/status?pageNumber=1&pageSize=20
Host: api-external.monitorqa.com
X-API-KEY: abcdef12345
```

## Response

### Webhook Command Types
- `0` - Audit
- `1` - Corrective Action
- `2` - Audit Template

**Success Response**

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "data": [
    {
      "createdAtUtc": "2024-06-06T10:34:26.493Z",
      "errorMessage": "Connection timeout",
      "webhookCommandType": 0,
      "httpStatusCode": 404,
      "webhookUrl": "https://your-webhook-endpoint.com/audit",
      "webhookEvent": "AUDIT_ASSIGNED"
    },
    {
      "createdAtUtc": "2024-06-06T09:15:12.156Z",
      "errorMessage": null,
      "webhookCommandType": 1,
      "httpStatusCode": 200,
      "webhookUrl": "https://your-webhook-endpoint.com/corrective-action",
      "webhookEvent": "CORRECTIVE_ACTION_CREATED"
    }
  ],
  "meta": {
    "pageNumber": 1,
    "pageSize": 20,
    "totalCount": 150
  }
}
```


For errors responses, see the [response status codes documentation](#/response-status-codes).
