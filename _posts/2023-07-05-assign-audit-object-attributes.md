---
category: 5. Audit Objects
url_path: '/audit/objects/{id}/attributes'
title: 'Assign Attributes to Audit Object'
type: 'POST'
order: 1
layout: null
---

Assign multiple attributes to a specific audit object. This endpoint allows you to categorize and tag audit objects with custom attributes for better organization and filtering. Duplicate assignments are ignored, and invalid options will not be assigned.

## Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| id | string | Yes | The unique identifier of the audit object |
| attributes | array[object] | Yes | Array of attribute-option pairs to assign |
| attributes[].attributeId | string | Yes | The ID of the attribute |
| attributes[].optionId | string | Yes | The ID of the specific option within the attribute |

## Request Example

```http
POST https://api-external.monitorqa.com/audit/objects/{id}/attributes
X-API-KEY: abcdef12345
Content-Type: application/json

{
  "attributes": [
    {
      "attributeId": "attr-dept-001",
      "optionId": "option-manufacturing"
    },
    {
      "attributeId": "attr-priority-001",
      "optionId": "option-high"
    },
    {
      "attributeId": "attr-equipment-001",
      "optionId": "option-heavy-machinery"
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
