---
category: 1. General
url_path: '/status-codes'
title: 'Status Codes'
order: 5

layout: null
---

### HTTP Status Codes

The MonitorQA API uses standard HTTP status codes to indicate the success or failure of API requests. Below are the common status codes you may encounter:

#### Success Codes

| Status Code | Description | Usage |
|-------------|-------------|-------|
| `200 OK` | Request successful | Returned for successful GET, PUT, and POST requests |
| `201 Created` | Resource created successfully | Returned when a new resource is created |
| `204 No Content` | Request successful, no content to return | Typically returned for successful DELETE requests |

#### Client Error Codes

| Status Code | Description | Common Causes |
|-------------|-------------|---------------|
| `400 Bad Request` | Invalid request format or parameters | Malformed JSON, missing required fields, invalid parameter values |
| `401 Unauthorized` | Authentication required or invalid | Missing or invalid `X-API-KEY` header |
| `403 Forbidden` | Access denied | Valid authentication but insufficient permissions for the resource |
| `404 Not Found` | Resource not found | Invalid endpoint URL or resource ID doesn't exist |
| `409 Conflict` | Resource conflict | Attempting to create a resource that already exists |
| `422 Unprocessable Entity` | Validation errors | Request format is correct but contains invalid data |

#### Server Error Codes

| Status Code | Description | Action |
|-------------|-------------|--------|
| `500 Internal Server Error` | Unexpected server error | Contact support if error persists |
| `502 Bad Gateway` | Gateway error | Temporary issue, retry request |
| `503 Service Unavailable` | Service temporarily unavailable | Retry request after delay |

#### Error Response Format

When an error occurs, the API returns a JSON response with error details:

```json
{
  "error": {
    "message": "Description of the error",
    "code": "ERROR_CODE",
    "details": {
      "field": "Additional error context"
    }
  }
}
```
