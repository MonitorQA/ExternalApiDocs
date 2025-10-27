---
category: 5. Audit Objects
url_path: '/audit/objects/{id}/attributes'
title: 'Delete Attributes Assignments from Audit Object'
type: 'DELETE'
order: 7
layout: null
---

Remove specific attribute assignments from an audit object. This endpoint allows you to unassign particular attribute-option combinations while leaving other assignments intact. Invalid attribute or option IDs are silently ignored.

## Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| id | string | Yes | The unique identifier of the audit object |
| attributes | array[object] | Yes | Array of attribute-option pairs to remove |
| attributes[].attributeId | string | Yes | The ID of the attribute |
| attributes[].optionId | string | Yes | The ID of the specific option within the attribute |

### Example Request

```http
DELETE /audit/objects/{id}/attributes
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


For errors responses, see the [response status codes documentation](#/response-status-codes).
