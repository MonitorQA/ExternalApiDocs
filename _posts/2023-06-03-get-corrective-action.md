---
category: 10. Corrective Actions
categoryOrder: 10
url_path: '/corrective-actions/{id}'
title: 'Get corrective action details'
type: 'GET'
order: 4
layout: null
---

Retrieve detailed information about a specific corrective action, including its status, assignees, files, and related audit information.

### Request Headers

| Header | Type | Required | Description |
|--------|------|----------|-------------|
| `X-API-KEY` | string | Yes | API authentication key |

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

## Response

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

**Success Response**

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
   "answer": {
      "name": "Fire extinguisher inspection",
      "points": 5,
      "text": "Fire extinguisher is missing from designated location",
      "number": 3,
      "isFailed": true
   },
   "approvedAtUtc": "2023-11-15T14:30:22.123Z",
   "approvedBy": {
        "id": "a8f3d2c1-b4e5-4f6g-9h8i-1j2k3l4m5n6o", 
        "name": "Sarah Johnson"
      },
   "assignedUsers": [
      {
         "id": "b9e4c3d2-c5f6-5g7h-0i9j-2k3l4m5n6o7p",
         "name": "Mike Rodriguez"
      }
   ],
   "audit": {
      "id": "c0f5d4e3-d6g7-6h8i-1j0k-3l4m5n6o7p8q",
      "name": "Monthly Safety Inspection - Building A",
      "ianaTimeZone": "America/New_York"
   },
   "auditItemId": "d1g6e5f4-e7h8-7i9j-2k1l-4m5n6o7p8q9r",
   "auditObject": {
      "id": "e2h7f6g5-f8i9-8j0k-3l2m-5n6o7p8q9r0s",
      "name": "Building A - First Floor"
   },
   "createdAtUtc": "2023-10-31T11:05:37.688Z",
   "createdBy": {
      "id": "f3i8g7h6-g9j0-9k1l-4m3n-6o7p8q9r0s1t",
      "name": "John Smith"
   },
   "description": "Replace missing fire extinguisher in hallway near conference room 101",
   "dueDateUtc": "2023-11-01T06:59:59.000Z",
   "expiredAtUtc": "2023-11-03T06:59:59.000Z",
   "expiredBy": {
      "id": "g4j9h8i7-h0k1-0l2m-5n4o-7p8q9r0s1t2u",
      "name": "Lisa Chen"
   },
   "id": "h5k0i9j8-i1l2-1m3n-6o5p-8q9r0s1t2u3v",
   "information": {
      "text": "Fire extinguisher has been ordered and will be installed by facilities team",
      "photosIds": [
         "i6l1j0k9-j2m3-2n4o-7p6q-9r0s1t2u3v4w"
      ],
      "files": [
         {
            "id": "j7m2k1l0-k3n4-3o5p-8q7r-0s1t2u3v4w5x",
            "name": "fire_extinguisher_order_receipt.pdf",
            "contentType": "application/pdf",
            "updatedAt": "2023-11-02T09:15:33.456Z"
         }
      ]
   },
   "name": "Fire Extinguisher Replacement",
   "number": "CA-2023-001",
   "priority": 2,
   "question": "Is the fire extinguisher present and accessible?",
   "status": 3,
   "tags": [
      {
         "id": "k8n3l2m1-l4o5-4p6q-9r8s-1t2u3v4w5x6y",
         "name": "Fire Safety"
      }
   ],
   "files": [
      {
         "id": "l9o4m3n2-m5p6-5q7r-0s9t-2u3v4w5x6y7z",
         "name": "corrective_action_photos.jpg",
         "contentType": "image/jpeg",
         "updatedAt": "2023-10-31T11:05:37.688Z"
      }
   ]
}
```


For errors responses, see the [response status codes documentation](#/response-status-codes).
