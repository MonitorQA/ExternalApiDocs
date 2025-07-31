---
category: 5. Audit Objects
url_path: '/audit/object/{id}'
title: 'Get an audit object details'
type: 'GET'
order: 18
layout: null
---

Retrieve detailed information about a specific audit object, including its participants, attributes, and location data. This endpoint provides comprehensive audit object details needed for audit planning and execution.

## Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| id | string | Yes | The unique identifier of the audit object |

## Request Example

```http
GET https://api-external.monitorqa.com/audit/object/{id}
X-API-KEY: abcdef12345
```

## Response

**Success Response**

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "id": "object-123",
  "name": "Manufacturing Line A",
  "notes": "Primary production line for automotive parts",
  "participantUserGroups": [
    {
      "id": "group-456",
      "name": "Production Supervisors"
    }
  ],
  "participantUsers": [
    {
      "id": "user-789",
      "name": "John Smith"
    }
  ],
  "auditObjectGroupIds": [
    "group-manufacturing"
  ],
  "attributes": [
    {
      "attributeId": "attr-001",
      "attributeName": "Department",
      "optionId": "opt-production",
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
