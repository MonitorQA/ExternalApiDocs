---
category: Company
categoryOrder: 14
url_path: '/company/icon'
title: 'Delete company icon'
type: 'DELETE'
order: 6
layout: null
---

Remove the company icon. This action permanently deletes the icon from the company profile.

### Request Headers

| Header | Type | Required | Description |
|--------|------|----------|-------------|
| `X-API-KEY` | string | Yes | API authentication key |

### Example Request

```http
DELETE /company/icon
Host: api-external.monitorqa.com
X-API-KEY: abcdef12345
```

## Response

**Success Response**

```http
HTTP/1.1 200 OK
```

Empty response body indicates successful icon deletion.

For errors responses, see the [response status codes documentation](#/response-status-codes).

