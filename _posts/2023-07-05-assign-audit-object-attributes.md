---
category: 5. Audit objects
categoryOrder: 5
url_path: '/audit/objects/{id}/attributes'
title: 'Assign Attributes to Audit Object'
type: 'POST'
order: 6
layout: null
---

Assign multiple attributes to a specific audit object. This endpoint enables categorizing and tagging audit objects with custom attributes for better organization and filtering. Duplicate assignments are ignored, and invalid options will not be assigned.

## Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| id | string | Yes | The unique identifier of the audit object |
| attributes | array[object] | Yes | Array of attribute-option pairs to assign |
| attributes[].attributeId | string | Yes | The ID of the attribute |
| attributes[].optionId | string | Yes | The ID of the specific option within the attribute |

### Example Request

```http
POST /audit/objects/{id}/attributes
Host: api-external.monitorqa.com
X-API-KEY: abcdef12345
Content-Type: application/json

{
  "attributes": [
    {
      "attributeId": "890123de-fghi-4567-890a-bcdef1234567",
      "optionId": "678901bc-defa-2345-6789-01bcdef12345"
    },
    {
      "attributeId": "901234ef-ghij-5678-90ab-cdef12345678",
      "optionId": "789012cd-efab-3456-789a-12cdef123456"
    },
    {
      "attributeId": "012345fg-hijk-6789-01bc-def123456789",
      "optionId": "123456gh-ijkl-789a-bcde-f12345678901"
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


For errors responses, see the [response status codes documentation](#/response-status-codes).
