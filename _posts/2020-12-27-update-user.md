---
category: 7. Users
url_path: '/users'
title: 'Update user'
type: 'PUT'
order: 25
layout: null
---

This method allows to update company user

### Request

* The headers must include a **valid api key**.
* The body must include user data.
* **`fullName`** is user name, **required**.
* **`roleId`** is user role id, optional. If not specified user role won't be changed.
* **`phone`** is user phone, optional, **max length is 50 chracters**.


```X-API-KEY:  abcdef12345```

```{
  "email": "string",
  "roleId": "string",
  "phone": string  
}```

### Response

**If succeeds**, returns empty response

```Status: 200 OK```

For errors responses, see the [response status codes documentation](#/response-status-codes).
