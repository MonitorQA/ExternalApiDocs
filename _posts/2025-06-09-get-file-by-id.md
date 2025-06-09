---
category: 13. Files
url_path: '/files/{id}'
title: 'Get File'
type: 'GET'
order: 1
layout: null
---

This method allows to get file by it's unique id.

### Request

* **`{id}`** is the id of file, **required**.
* The headers must include a **valid api key**.

```X-API-KEY:  abcdef12345```

### Optional Query String Parameters
* **`withWatermark`** is flag to get file with watermark. Set to `true` to get image file with watermark. It will return original file when watermark is disabled in template settings.

### Response

**If succeeds**, returns file content.

```Status: 200 OK```


For errors responses, see the [response status codes documentation](#/response-status-codes).
