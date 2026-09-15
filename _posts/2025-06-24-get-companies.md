---
category: Company
categoryOrder: 14
url_path: '/company/accessible'
title: 'Get accessible companies'
type: 'GET'
order: 4
layout: null
---

Retrieve a list of all companies accessible to the authenticated user. This endpoint returns all companies where the user has an account. This is useful for users who have access to multiple companies and need to switch between them, select a target company for [template copying](#/copy-template) operations, or pass company IDs as the `companies` filter on [custom data exports](#/custom-data-exports). For custom data exports, the API key user must also have [`dataExports.accessCustom`](#/role-permissions-reference) in each company included in the export.

### Request Headers

| Header | Type | Required | Description |
|--------|------|----------|-------------|
| `X-API-KEY` | string | Yes | API authentication key |

### Example Request

```http
GET /company/accessible
Host: api-external.monitorqa.com
X-API-KEY: abcdef12345
```

## Response

**Success Response**

```http
HTTP/1.1 200 OK
Content-Type: application/json

[
  {
    "id": "123e4567-e89b-12d3-a456-426614174000",
    "name": "Acme Manufacturing Corp"
  },
  {
    "id": "234e5678-e89b-12d3-a456-426614174004",
    "name": "Quality Control Inc"
  }
]
```

### Response Fields

| Field | Type | Description |
|-------|------|-------------|
| `id` | uuid | The unique identifier of the company |
| `name` | string | The company name |

For error responses, see the [response status codes documentation](#/response-status-codes).

