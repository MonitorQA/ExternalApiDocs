---
category: Company
categoryOrder: 14
url_path: '/company/logo'
title: 'Upload company logo'
type: 'POST'
order: 3
layout: null
---

Upload a logo image for the company. Supported image formats: **BMP, PNG, GIF, JPEG** (content types: `image/bmp`, `image/png`, `image/gif`, `image/jpeg`, `image/jpg`).

### Request Headers

| Header | Type | Required | Description |
|--------|------|----------|-------------|
| `X-API-KEY` | string | Yes | API authentication key |
| `Content-Type` | string | Yes | Must be `multipart/form-data` |

### Request Body

The request must be a multipart form-data upload containing a single image file.

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| File | file | Yes | The logo image file to upload. Must include a `Content-Type` header set to one of: `image/bmp`, `image/png`, `image/gif`, `image/jpeg`, or `image/jpg` |

### Example Request

```http
POST /company/logo
Host: api-external.monitorqa.com
X-API-KEY: abcdef12345
Content-Type: multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW

------WebKitFormBoundary7MA4YWxkTrZu0gW
Content-Disposition: form-data; name="file"; filename="logo.png"
Content-Type: image/png

[Binary file content]
------WebKitFormBoundary7MA4YWxkTrZu0gW--
```

## Response

**Success Response**

```http
HTTP/1.1 200 OK
```

Empty response body indicates successful logo upload.

**Error Responses**

The API will return `400 Bad Request` in the following cases:
- `Content-Type` header is missing from the request
- File `Content-Type` is missing or not one of the allowed image types
- The request couldn't be processed

For other error responses, see the [response status codes documentation](#/response-status-codes).

