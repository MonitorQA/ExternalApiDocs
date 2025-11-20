---
category: 14. Company
categoryOrder: 14
url_path: '/company'
title: 'Get company information'
type: 'GET'
order: 1
layout: null
---

Retrieve basic information about the company account. This endpoint provides essential company details including the unique company identifier, display name, file identifiers for uploaded logo and icon images, usage purpose, and custom audit object name.

### Example Request

```http
GET /company
Host: api-external.monitorqa.com
X-API-KEY: abcdef12345
```

## Response

**Success Response**

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "id": "456789jk-lmno-012b-cdef-123456789012",
  "name": "Acme Manufacturing Corp",
  "logoFileId": "123e4567-e89b-12d3-a456-426614174000",
  "iconFileId": "789e4567-e89b-12d3-a456-426614174001",
  "usagePurpose": 0,
  "customAuditObjectName": null
}
```

**Example Response (Other Usage Purpose)**

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "id": "456789jk-lmno-012b-cdef-123456789012",
  "name": "Custom Company Inc",
  "logoFileId": null,
  "iconFileId": null,
  "usagePurpose": 6,
  "customAuditObjectName": "Facility"
}
```

### Response Fields

| Field | Type | Description |
|-------|------|-------------|
| `id` | uuid | The unique identifier of the company |
| `name` | string | The company name |
| `logoFileId` | uuid | Optional. The unique identifier of the company logo file, if a logo has been uploaded |
| `iconFileId` | uuid | Optional. The unique identifier of the company icon file, if an icon has been uploaded |
| `usagePurpose` | number | Optional. The primary usage purpose for the company. Valid values: `0` (Locations), `1` (Stores), `2` (Sites), `3` (Machines), `4` (Plants), `5` (Vehicles), `6` (Other), `7` (Processes) |
| `customAuditObjectName` | string | Optional. Custom name for the audit object type when `usagePurpose` is `6` (Other) |

For errors responses, see the [response status codes documentation](#/response-status-codes).
