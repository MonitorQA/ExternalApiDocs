---
category: 5. Audit Objects
url_path: '/audit/objects'
title: 'Create a new audit object'
type: 'POST'
order: 3
layout: null
---

This method allows you to create a new audit object with specified properties including name, notes, and geographic location.

### Request Headers

| Header | Type | Required | Description |
|--------|------|----------|-------------|
| `X-API-KEY` | string | Yes | Your API authentication key |
| `Content-Type` | string | Yes | Must be `application/json` |

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
POST /audit/objects
Host: api-external.monitorqa.com
X-API-KEY: abcdef12345
Content-Type: application/json

{

  "name": "Warehouse Section A",
  "notes": "Storage area for temperature-sensitive materials",
  "geoAddress": {
    "lat": "40.7128",
    "lng": "-74.0060",
    "name": "Warehouse Building",
    "address": "456 Industrial Blvd, New York, NY 10002"
  }
}
```

## Response

**Success Response**

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "id": "a1b2c3d4-e5f6-789a-bcde-f01234567890"   
}
```

For errors responses, see the [response status codes documentation](#/response-status-codes).
