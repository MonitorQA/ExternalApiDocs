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

* **assignedUsersIds** - array of user ids 
* **description** - corrective action decription
* **name** - corrective action name *required*
* **dueDateUtc** - corrective action due date *required*
* **status** - corrective action status *required*
* **priority** - corrective action priority *required*

```{
   "assignedUsersIds": [string],
   "description": string,
   "name": string,
   "dueDateUtc": date,
   "status": 0,
   "priority": 0
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
