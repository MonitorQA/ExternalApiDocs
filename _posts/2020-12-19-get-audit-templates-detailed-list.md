---
category: 4. Audit Templates
url_path: '/audit/templates/detailed'
title: 'Get audit templates detailed list'
type: 'GET'
order: 16
layout: null
---

This method allows to get audit templates detailed list.

### Request
* The headers must include a **valid api key**.

```X-API-KEY:  abcdef12345```

### Optional Query String Parameters
* **`templateType`** - filter by template type.
* **`search`** - filter by template name.
* **`orderBy`** - apply ordering to result list.
* **`orderByDirection`** - control ordering direction in result list.
* **`pageNumber`** - current page number, starts from 1.
* **`pageSize`** - current page size.

### Response

**If succeeds**, returns a detailed list of audit templates.

```Status: 200 OK```

```{
  "data": [
    {
      "id": "string",
      "name": "string",
      "isDraft": true,
      "templateType": 0
    }
  ],
  "meta": {
    "pageNumber": 0,
    "pageSize": 0,
    "totalCount": 0
  }
}```

For errors responses, see the [response status codes documentation](#/response-status-codes).
