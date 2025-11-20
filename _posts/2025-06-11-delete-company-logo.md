---
category: 14. Company
categoryOrder: 14
url_path: '/company/logo'
title: 'Delete company logo'
type: 'DELETE'
order: 4
layout: null
---

Remove the company logo. This action permanently deletes the logo from the company profile.

### Request Headers

| Header | Type | Required | Description |
|--------|------|----------|-------------|
| `X-API-KEY` | string | Yes | API authentication key |

### Example Request

```http
DELETE /company/logo
Host: api-external.monitorqa.com
X-API-KEY: abcdef12345
```

## Response

**Success Response**

```http
HTTP/1.1 200 OK
```

Empty response body indicates successful logo deletion.

For errors responses, see the [response status codes documentation](#/response-status-codes).

