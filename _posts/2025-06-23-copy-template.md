---
category: Audit Templates
categoryOrder: 4
url_path: '/audit/templates/copy'
title: 'Copy template to another company'
type: 'POST'
order: 4
layout: null
---

Copy a published audit template from the current authorized company to another company where the authenticated user has access. The template will be copied as a published template and associated with a score system in the target company.

**Prerequisites:**
- The source template must exist in the current authorized company (the company associated with the API key used for authentication)
- The authenticated user must have template management permissions in the current authorized company
- The authenticated user must have an account in the target company
- The authenticated user must have template management permissions in the target company
- If `copyScoreSystem` is `false`, the target company must have at least one score system

### Request Headers

| Header | Type | Required | Description |
|--------|------|----------|-------------|
| `X-API-KEY` | string | Yes | API authentication key |
| `Content-Type` | string | Yes | Must be `application/json` |

### Request Body Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `templateId` | uuid | Yes | The unique identifier of the source template to copy from the current authorized company |
| `targetCompanyId` | uuid | Yes | The unique identifier of the target company where the template will be copied. Use the [Get accessible companies](#/get-companies) endpoint to retrieve a list of companies accessible to the authenticated user |
| `copyScoreSystem` | boolean | Yes | If `true`, the score system from the source template will be copied to the target company along with all its elements, and the copied template will use this new score system. If `false`, the copied template will be linked to the default score system in the target company |

### Example Request (Copy with Default Score System)

```http
POST /audit/templates/copy
Host: api-external.monitorqa.com
X-API-KEY: abcdef12345
Content-Type: application/json

{
  "templateId": "567890ab-cdef-1234-5678-90abcdef1234",
  "targetCompanyId": "123e4567-e89b-12d3-a456-426614174000",
  "copyScoreSystem": false
}
```

### Example Request (Copy with Source Score System)

```http
POST /audit/templates/copy
Host: api-external.monitorqa.com
X-API-KEY: abcdef12345
Content-Type: application/json

{
  "templateId": "567890ab-cdef-1234-5678-90abcdef1234",
  "targetCompanyId": "123e4567-e89b-12d3-a456-426614174000",
  "copyScoreSystem": true
}
```

## Response

**Success Response**

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "templateId": "98765432-1234-5678-90ab-cdef12345678"
}
```

### Response Fields

| Field | Type | Description |
|-------|------|-------------|
| `templateId` | uuid | The unique identifier of the newly copied template in the target company |

The response contains the unique identifier of the copied template. The template is now available in the target company and can be used for creating audits.

**Note:** All files associated with the template (such as images) are also copied to the target company. When `copyScoreSystem` is `true`, a new score system is created in the target company with all its elements (labels, colors, thresholds) copied from the source template's score system.

### Error Responses

**Template Not Found (409)**

```http
HTTP/1.1 409 Conflict
Content-Type: application/json

{
  "message": "template/not-found"
}
```

**Template Not Accessible (409)**

```http
HTTP/1.1 409 Conflict
Content-Type: application/json

{
  "message": "template/not-accessible"
}
```

Occurs when the source template does not exist in the current authorized company (the company associated with the API key used for authentication).

**Company Not Accessible (409)**

```http
HTTP/1.1 409 Conflict
Content-Type: application/json

{
  "message": "company/not-accessible"
}
```

Occurs when the authenticated user does not have an account in the target company.

**Permissions Error (409)**

```http
HTTP/1.1 409 Conflict
Content-Type: application/json

{
  "message": "permissions/can-manage-templates"
}
```

Occurs when the authenticated user does not have template management permissions in the current authorized company or target company.

**No Default Score System (409)**

```http
HTTP/1.1 409 Conflict
Content-Type: application/json

{
  "message": "score-system/no-default-score-system"
}
```

Occurs when `copyScoreSystem` is `false` and the target company does not have at least one score system.

For errors responses, see the [response status codes documentation](#/response-status-codes).

