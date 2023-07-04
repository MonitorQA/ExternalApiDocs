---
category: Corrective Actions
url_path: '/corrective-actions/{id}'
title: 'Update corrective action details'
type: 'PUT'

layout: null
---

This method allows to update details of corrective action.

### Request

* **`{id}`** is the id of corrective action, **required**.
* The headers must include a **valid api key**.

Null-value fields are ignored on update

```{
   "AssignedUsersIds": [string],
   "Description": string,
   "Name": string,
   "DueDateUtc": date,
   "Status": 0,
   "Priority": 0
}```

### Response

Possible corrective action statuses:

```   0 - Open,
  1 - Approved,
  2 - Rejected,
  3 - Submitted,
  4 - Expired```

Possible corrective action priorities:

```   0 - Low,
  1 - Medium,
  2 - High```

**If succeeds**, returns empty response

```Status: 200 OK```


For errors responses, see the [response status codes documentation](#/response-status-codes).
