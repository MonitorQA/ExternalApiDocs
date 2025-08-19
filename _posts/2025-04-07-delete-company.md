---
category: 8. Company Information
url_path: '/company'
title: 'Delete company'
type: 'DELETE'
order: 26
layout: null
---

**⚠️ DANGER ZONE ⚠️**

Permanently delete your entire company account from the MonitorQA system. This is an irreversible action that will completely remove all data associated with your organization.

## ⚠️ WARNING: This action cannot be undone!

Deleting your company account will:
- **Cancel your active subscription immediately**
- **Remove all company users and revoke their access**
- **Delete all audits, schedules, and historical data**
- **Remove all audit objects, templates, and configurations**
- **Delete all corrective actions and related records**
- **Stop all future billing charges**

### Example Request

```http
DELETE /company
Host: api-external.monitorqa.com
X-API-KEY: abcdef12345
```

## Response

**Success Response**

```http
HTTP/1.1 200 OK
```

Empty response body indicates successful account deletion. Your API key will be immediately invalidated after this operation.

For errors responses, see the [response status codes documentation](#/response-status-codes).
