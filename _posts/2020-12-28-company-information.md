---
category: 8. Company Information
url_path: '/company'
title: 'Get company information'
type: 'GET'
order: 25
layout: null
---

Retrieve basic information about your company account. This endpoint provides essential company details including the unique company identifier and display name.

## Request Example

```http
GET https://api-external.monitorqa.com/company
X-API-KEY: abcdef12345
```

## Response

**Success Response**

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "id": "company-123",
  "name": "Acme Manufacturing Corp"
}
```

For errors responses, see the [response status codes documentation](#/response-status-codes).
