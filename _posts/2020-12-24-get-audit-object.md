---
category: 5. Audit objects
categoryOrder: 5
url_path: '/audit/object/{id}'
title: 'Get an audit object details'
type: 'GET'
order: 5
layout: null
---

Retrieve detailed information about a specific audit object, including its participants, attributes, and location data. This endpoint provides comprehensive audit object details needed for audit planning and execution.

## Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| id | string | Yes | The unique identifier of the audit object |

### Example Request

```http
GET /audit/object/123e4567-e89b-12d3-a456-426614174000
Host: api-external.monitorqa.com
X-API-KEY: abcdef12345
```

## Response

**Success Response**

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "id": "789abcde-f123-4567-8901-234567890123",
  "name": "Manufacturing Line A",
  "notes": "Primary production line for automotive parts",
  "participantUserGroups": [
    {
      "id": "123456gh-ijkl-789a-bcde-f12345678901",
      "name": "Production Supervisors"
    }
  ],
  "participantUsers": [
    {
      "id": "123e4567-e89b-12d3-a456-426614174000",
      "name": "John Smith"
    }
  ],
  "auditObjectGroupIds": [
    "234567hi-jklm-890a-bcde-f12345678902"
  ],
  "attributes": [
    {
      "attributeId": "890123de-fghi-4567-890a-bcdef1234567",
      "attributeName": "Department",
      "optionId": "678901bc-defa-2345-6789-01bcdef12345",
      "optionName": "Production"
    }
  ],
  "geoAddress": {
    "lat": "40.7128",
    "lng": "-74.0060",
    "name": "Factory Floor A",
    "address": "123 Industrial Ave, Manufacturing City, MC 12345"
  }
}
```

For errors responses, see the [response status codes documentation](#/response-status-codes).
