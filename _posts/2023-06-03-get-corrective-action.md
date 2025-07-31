---
category: 9. Corrective Actions
url_path: '/corrective-actions/{id}'
title: 'Get corrective action details'
type: 'GET'
order: 4
layout: null
---

This method allows you to retrieve detailed information about a specific corrective action, including its status, assignees, files, and related audit information.

### Request Headers

| Header | Type | Required | Description |
|--------|------|----------|-------------|
| `X-API-KEY` | string | Yes | Your API authentication key |

### Path Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `id` | string | Yes | Unique identifier of the corrective action |

### Example Request

```http
GET /corrective-actions/123e4567-e89b-12d3-a456-426614174000
Host: api-external.monitorqa.com
X-API-KEY: abcdef12345
```

### Response

#### Status Values

| Value | Status | Description |
|-------|--------|-------------|
| `0` | Open | Corrective action is open and pending work |
| `1` | Approved | Corrective action has been approved |
| `2` | Rejected | Corrective action has been rejected |
| `3` | Submitted | Corrective action has been submitted for review |
| `4` | Expired | Corrective action has expired without completion |

#### Priority Values

| Value | Priority | Description |
|-------|----------|-------------|
| `0` | Low | Low priority corrective action |
| `1` | Medium | Medium priority corrective action |
| `2` | High | High priority corrective action |

**If succeeds**, returns corrective action details.

```Status: 200 OK```

```{
   "answer": {
      "name": string,
      "points": number,
      "text": string,
      "number": number,
      "isFailed": boolean
   },
   "approvedAtUtc": date,
   "approvedBy": {
        "id": string, 
        "name": string
      },
   "assignedUsers": [
      {
         "id": string,
         "name": string
      }
   ],
   "audit": {
      "id": string,
      "name": string,
      "ianaTimeZone": string
   },
   "auditItemId": string,
   "auditObject": {
      "id": string,
      "name": string
   },
   "createdAtUtc": "2022-10-31T11:05:37.6888585",
   "createdBy": {
      "id": string,
      "name": string
   },
   "description": string,
   "dueDateUtc": "2022-11-01T06:59:59",
   "expiredAtUtc": date,
   "expiredBy": {
      "id": string,
      "name": string
   },
   "id": string,
   "information": {
      "text": string,
      "photosIds": [
         string
      ],
      "files": [
         {
            "id": string,
            "name": string,
            "contentType": string,
            "updatedAt": "2023-07-03T11:31:01.8187649Z"
         }
      ]
   },
   "name": string,
   "number": string,
   "priority": 0,
   "question": string,
   "status": 3,
   "tags": [
      {
         "id": string,
         "name": string
      }
   ],
   "files": [
      {
         "id": string,
         "name": string,
         "contentType": string,
         "updatedAt": "2022-10-31T11:05:37.6887695Z"
      }
   ]
}```


For errors responses, see the [response status codes documentation](#/response-status-codes).
