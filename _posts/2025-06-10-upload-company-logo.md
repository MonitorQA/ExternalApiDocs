---
category: 13. Company
url_path: '/company/logo'
title: 'Upload company logo'
type: 'POST'
order: 3
layout: null
---

Upload a logo image for the company. Supported image formats include JPEG, PNG, and other common image types.

### Request Headers

| Header | Type | Required | Description |
|--------|------|----------|-------------|
| `X-API-KEY` | string | Yes | API authentication key |
| `Content-Type` | string | Yes | Must be `multipart/form-data` |

### Request Body

The request must be a multipart form-data upload containing a single image file.

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| File | file | Yes | The logo image file to upload |

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

For errors responses, see the [response status codes documentation](#/response-status-codes).

