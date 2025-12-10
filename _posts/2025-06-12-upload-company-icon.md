---
category: Company
categoryOrder: 14
url_path: '/company/icon'
title: 'Upload company icon'
type: 'POST'
order: 5
layout: null
---

Upload an icon image for the company. Supported image formats: **PNG, JPEG** (content types: `image/png`, `image/jpeg`, `image/jpg`).

### Request Headers

| Header | Type | Required | Description |
|--------|------|----------|-------------|
| `X-API-KEY` | string | Yes | API authentication key |
| `Content-Type` | string | Yes | Must be `multipart/form-data` |

### Request Body

The request must be a multipart form-data upload containing a single image file.

> **Note:** Only the first file in the request body will be processed. Any additional files will be ignored.

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| File | file | Yes | The icon image file to upload. Must include a `Content-Type` header set to one of: `image/png`, `image/jpeg`, or `image/jpg` |

### Example Request

```http
POST /company/icon
Host: api-external.monitorqa.com
X-API-KEY: abcdef12345
Content-Type: multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW

------WebKitFormBoundary7MA4YWxkTrZu0gW
Content-Disposition: form-data; name="file"; filename="icon.png"
Content-Type: image/png

[Binary file content]
------WebKitFormBoundary7MA4YWxkTrZu0gW--
```

## Response

**Success Response**

```http
HTTP/1.1 200 OK
```

Empty response body indicates successful icon upload.

**Error Responses**

The API will return `400 Bad Request` in the following cases:
- `Content-Type` header is missing from the request
- File `Content-Type` is missing or not one of the allowed image types
- The request couldn't be processed

For other error responses, see the [response status codes documentation](#/response-status-codes).

