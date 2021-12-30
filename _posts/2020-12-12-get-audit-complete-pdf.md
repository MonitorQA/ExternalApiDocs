---
category: Audit
url_path: '/audit/complete/{auditId}/report-pdf'
title: 'Get audit pdf report'
type: 'GET'

layout: null
---

This method allows to get pdf report of complete audit.

### Request
* **`{auditId}`** is id of complete audit, **required**.
* The headers must include a **valid api key**.

```X-API-KEY:  abcdef12345```

### Optional Query String Parameters
* **`locale`** is report locale.
* **`reportType`** is report type.
* **`includePhotos`** is flag used to include photos into report.


### Response

**If succeeds**, returns pdf file with complete audit report.

```Status: 200 OK```

For errors responses, see the [response status codes documentation](#/response-status-codes).
