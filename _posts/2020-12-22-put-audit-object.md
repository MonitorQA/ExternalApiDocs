---
category: 5. Audit Objects
url_path: '/audit/objects/{id}'
title: 'Update an audit object'
type: 'PUT'
order: 20
layout: null
---

This method allows you to update an existing audit object with new information including name, notes, and geographic location.

### Request Headers

| Header | Type | Required | Description |
|--------|------|----------|-------------|
| `X-API-KEY` | string | Yes | Your API authentication key |
| `Content-Type` | string | Yes | Must be `application/json` |

### Path Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `id` | string | Yes | Unique identifier of the audit object |

### Request Body Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `name` | string | Yes | Audit object name |
| `notes` | string | No | Notes visible to auditor during audit (max 800 characters) |
| `geoAddress` | object | No | Geographic address information (all fields required when provided) |
| `geoAddress.lat` | string | No | Latitude coordinate |
| `geoAddress.lng` | string | No | Longitude coordinate |
| `geoAddress.name` | string | No | Location name |
| `geoAddress.address` | string | No | Street address |

### Example Request

```http
PUT /audit/objects/{id}
Host: api-external.monitorqa.com
X-API-KEY: abcdef12345
Content-Type: application/json

{

  "name": "Main Production Facility",
  "notes": "Located on the second floor, requires safety equipment",
  "geoAddress": {
    "lat": "40.7128",
    "lng": "-74.0060",
    "name": "Main Building",
    "address": "123 Business Park Dr, New York, NY 10001"
  }
}
```

## Response

**Success Response**

```http
HTTP/1.1 200 OK
```

For errors responses, see the [response status codes documentation](#/response-status-codes).
