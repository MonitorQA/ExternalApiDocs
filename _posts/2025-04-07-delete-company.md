---
category: 8. Company Information
url_path: '/company'
title: 'Delete company'
type: 'DELETE'
order: 26
layout: null
---

This method allows to permanently delete the company account.

**This action can't be undone!** Deleting your account will:

Cancel all active subscriptions:

* No further charges will be applied

Affect all organization members:

* All users will lose access immediately

* Pending invitations will be canceled

### Request

* The headers must include a **valid api key**.

### Response

Returns empty response

```Status: 200 OK```

For errors responses, see the [response status codes documentation](#/response-status-codes).
