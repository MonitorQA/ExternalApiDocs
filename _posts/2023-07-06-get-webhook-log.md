---
category: 11. Webhook Log
url_path: '/webhooks/status'
title: 'Get webhooks log'
type: 'GET'
order: 1
layout: null
---

This method allows to get history of executed webhooks.

### Request
* The headers must include a **valid api key**.

### Optional Query String Parameters
* **`pageNumber`** - current page number, starts from 1.
* **`pageSize`** - current page size.

```X-API-KEY:  abcdef12345```

### Response

**If succeeds**, returns list of log records.

**Webhook Command Types**
* 0 - Audit
* 1 - Corrective Action
* 2 - Audit Template

```{
  "data": [
    {
        "createdAtUtc": "2024-06-06T10:34:26.4935581",
        "errorMessage": string,
        "webhookCommandType": 0,
        "httpStatusCode": 404,
        "webhookUrl": "https://123.mock.pstmn.io/",
        "webhookEvent": "AUDIT_ASSIGNED"
    },
  ],
  "meta": {
    "pageNumber": 0,
    "pageSize": 0,
    "totalCount": 0
  }
}```

```Status: 200 OK```


For errors responses, see the [response status codes documentation](#/response-status-codes).
