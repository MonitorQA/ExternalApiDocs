---
category: 8. Company Information
url_path: '/company'
title: 'Get company information'
type: 'GET'
order: 25
layout: null
---

Retrieve basic information about your company account. This endpoint provides essential company details including the unique company identifier and display name.

### Example Request

```http
GET /company
Host: api-external.monitorqa.com
X-API-KEY: abcdef12345
```

## Response

**Success Response**

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "id": "456789jk-lmno-012b-cdef-123456789012",
  "name": "Acme Manufacturing Corp"
}
```

For errors responses, see the [response status codes documentation](#/response-status-codes).
