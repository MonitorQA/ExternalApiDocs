---
category: 2. Audits
url_path: '/audit/complete/{auditId}/report'
title: 'Get audit report'
type: 'GET'
order: 10
layout: null
---

This method allows you to retrieve the detailed report of a completed audit, including all audit items, their statuses, and associated corrective actions.

### Request Headers

| Header | Type | Required | Description |
|--------|------|----------|-------------|
| `X-API-KEY` | string | Yes | Your API authentication key |

### Path Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `auditId` | string | Yes | Unique identifier of the completed audit |

### Example Request

```http
GET /audit/complete/{auditId}/report
Host: api-external.monitorqa.com
X-API-KEY: abcdef12345
```

### Response

**If succeeds**, returns complete audit items report.

```Status: 200 OK```

```{
   "id": "1acad6ca-cab8-48a7-07f2-08da929c74ab",
   "items": [
      {
         "id": "4ff6fbf7-8e6d-46be-356c-08da929d03c7",
         "text": string,
         "note": string,
         "notApplicable": boolean,
         "isCritical": boolean,
         "isPassed": boolean?,
         "childrenIds": [],
         "actions": [
            {
               "id": string,
               "name": string,
               "number": string,
               "description": "dd",
               "assignees": [
                    {
                        "id": string,
                        "name": string
                    }
                ],
               "comments": [],
               "createdBy": {
                  "id": "3c71b2a5-4c00-4bb0-9f08-785a2d8f7128",
                  "name": string
               },
               "createdAt": "2022-09-12T03:10:30.1333781",
               "dueDate": "2022-09-27T23:59:59.9999999",
               "priority": 0,
               "status": 0,
               "photos": [],
               "tags": []
            }
         ],
         "photos": [],
         "itemsCount": null,
         "points": null,
         "signature": null,
         "failedInRowCount": 1,
         "itemType": 2,
         "data": {
            "name": null,
            "points": 0.0000,
            "text": null,
            "number": 4.0000,
            "isFailed": true
         }
      }
   ]
}```

### Response Fields

**itemType** values:

| Value | Description |
|-------|-------------|
| `0` | Root |
| `1` | Section |
| `2` | Item |
| `3` | ConditionalItem |
| `4` | Condition |

**actions.priority** values:

| Value | Description |
|-------|-------------|
| `0` | Low |
| `1` | Medium |
| `2` | High |

**actions.status** values:

| Value | Description |
|-------|-------------|
| `0` | Open |
| `1` | Approved |
| `2` | Rejected |
| `3` | Submitted |

For errors responses, see the [response status codes documentation](#/response-status-codes).
