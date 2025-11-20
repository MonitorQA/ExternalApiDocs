---
category: 6. Audit object attributes
categoryOrder: 6
url_path: '/audit/objects/attributes'
title: 'Create Audit Object Attribute'
type: 'POST'
order: 3
layout: null
---

Create a new audit object attribute with multiple options. This endpoint enables defining custom attributes that can be assigned to audit objects for better categorization and filtering. At least one option must be provided, and the first option marked as default will be the default value.

## Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| name | string | Yes | The name of the attribute |
| options | array[object] | Yes | Array of available options (minimum 1 required) |
| options[].name | string | Yes | The name of the option |
| options[].isDefault | boolean | No | Whether this option is the default selection |

### Example Request

```http
POST /audit/objects/attributes
Host: api-external.monitorqa.com
X-API-KEY: abcdef12345
Content-Type: application/json

{
  "name": "Equipment Type",
  "options": [
    {
      "isDefault": true,
      "name": "Heavy Machinery"
    },
    {
      "isDefault": false,
      "name": "Safety Equipment"
    },
    {
      "isDefault": false,
      "name": "Measuring Instruments"
    }
  ]
}
```

## Response

**Success Response**

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "id": "345678ij-klmn-901a-bcde-f12345678903"
}
```

For errors responses, see the [response status codes documentation](#/response-status-codes).
