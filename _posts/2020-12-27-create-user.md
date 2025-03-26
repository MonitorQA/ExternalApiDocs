---
category: 7. Users
url_path: '/users'
title: 'Create user'
type: 'POST'
order: 24
layout: null
---

This method allows to create new company user

### Request

* The headers must include a **valid api key**.
* The body must include user data.
* **`email`** is user email, **required**.
* **`fullName`** is user name, **required**.
* **`roleId`** is user role id, **required**.
* **`phone`** is user phone, optional, **max length is 50 chracters**.


```X-API-KEY:  abcdef12345```

```{
  "fullName": "string",
  "email": "string",
  "roleId": "string",
  "phone": string  
}```

### Response

**If succeeds**, returns an id of created user.

```Status: 200 OK```
```{
    "id": "string"   
}```

For errors responses, see the [response status codes documentation](#/response-status-codes).
