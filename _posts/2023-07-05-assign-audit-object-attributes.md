---
category: Audit objects
categoryOrder: 5
url_path: '/audit/objects/{id}/attributes'
title: 'Assign Attributes to Audit Object'
type: 'POST'
order: 6
layout: null
---

Assign multiple attributes to a specific audit object. This endpoint enables categorizing and tagging audit objects with custom attributes for better organization and filtering. Duplicate assignments are ignored, and invalid options will not be assigned.

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
| `attributes` | array[object] | Yes | Array of attribute-option pairs to assign |
| `attributes[].attributeId` | uuid | Yes | The ID of the attribute |
| `attributes[].optionId` | uuid | Yes | The ID of the specific option within the attribute |

### Example Request

```http
POST /audit/objects/123e4567-e89b-12d3-a456-426614174000/attributes
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
    },
    {
      "attributeId": "012345f6-a012-6789-01bc-def123456789",
      "optionId": "123456a0-bcde-789a-bcde-f12345678901"
    }
  ]
}
```

## Response

**Success Response**

```http
HTTP/1.1 200 OK
```

Empty response body indicates successful assignment of attributes to the audit object.


For error responses, see the [response status codes documentation](#/response-status-codes).
