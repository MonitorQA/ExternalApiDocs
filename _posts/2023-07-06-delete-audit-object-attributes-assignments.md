---
category: Audit objects
categoryOrder: 5
url_path: '/audit/objects/{id}/attributes'
title: 'Delete attribute assignments from audit object'
type: 'DELETE'
order: 7
layout: null
---

Remove specific attribute assignments from an audit object. This endpoint enables unassigning particular attribute-option combinations while leaving other assignments intact. Invalid attribute or option IDs are silently ignored.

### Request Headers

| Header | Type | Required | Description |
|--------|------|----------|-------------|
| `X-API-KEY` | string | Yes | API authentication key |
| `Content-Type` | string | Yes | Must be `application/json` |

### Path Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `id` | uuid | Yes | The unique identifier of the audit object |

### Request Body Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `attributes` | array[object] | Yes | Array of attribute-option pairs to remove |
| `attributes[].attributeId` | uuid | Yes | The ID of the attribute |
| `attributes[].optionId` | uuid | Yes | The ID of the specific option within the attribute |

### Example Request

```http
DELETE /audit/objects/123e4567-e89b-12d3-a456-426614174000/attributes
Host: api-external.monitorqa.com
X-API-KEY: abcdef12345
Content-Type: application/json

{
  "attributes": [
    {
      "attributeId": "890123de-f012-4567-890a-bcdef1234567",
      "optionId": "678901bc-defa-2345-6789-01bcdef12345"
    },
    {
      "attributeId": "901234ef-a012-5678-90ab-cdef12345678",
      "optionId": "789012cd-efab-3456-789a-12cdef123456"
    }
  ]
}
```

## Response

**Success Response**

```http
HTTP/1.1 200 OK
```

Empty response body indicates successful removal of specified attribute assignments from the audit object.


For error responses, see the [response status codes documentation](#/response-status-codes).
