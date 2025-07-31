---
category: 10. Audit Object Attributes
url_path: '/audit/objects/attributes/{id}'
title: 'Update Audit Object Attribute'
type: 'PUT'
order: 4
layout: null
---

Update an existing audit object attribute and its options. This endpoint allows you to modify attribute names, add new options, update existing options, or remove options. Options with IDs will be updated, options without IDs will be created, and options not included in the request will be deleted.

## Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| id | string | Yes | The unique identifier of the audit object attribute to update |
| name | string | Yes | The updated name of the attribute |
| options | array[object] | Yes | Array of options (minimum 1 required) |
| options[].name | string | Yes | The name of the option |
| options[].isDefault | boolean | No | Whether this option is the default selection |
| options[].id | string | No | The ID of existing option to update (omit for new options) |

## Request Example

```http
PUT https://api-external.monitorqa.com/audit/objects/attributes/{id}
X-API-KEY: abcdef12345
Content-Type: application/json

{
  "name": "Updated Equipment Type",
  "options": [
    {
      "isDefault": true,
      "name": "Heavy Machinery",
      "id": "option-123"
    },
    {
      "isDefault": false,
      "name": "Safety Equipment",
      "id": "option-456"
    },
    {
      "isDefault": false,
      "name": "Electronic Equipment"
    }
  ]
}
```

## Response

**Success Response**

```http
HTTP/1.1 200 OK
```

Empty response body indicates successful attribute update.

**Note:** Options not included in the request will be permanently deleted, along with any audit object assignments using those options.

For errors responses, see the [response status codes documentation](#/response-status-codes).
