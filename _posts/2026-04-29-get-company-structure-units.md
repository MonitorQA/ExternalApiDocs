---
category: Company structure units
categoryOrder: 8
url_path: '/company-structure-units'
title: 'Get company structure units'
type: 'GET'
order: 1
layout: null
---

Retrieve a concise list of **company structure units** for the company. Each unit has an `id` and `name`. Use these IDs with request fields such as `assignedToUnit`, `auditObjectUnitIds`, and `assignedToUnitId`, and with list filters `auditObjectUnitId` (pending audits, complete audits, schedules) and `completedByUnit` (complete audits only). Deprecated query names `auditObjectGroupId` and `completedByGroup` are still accepted. When a filter refers to a unit on the **user** side, the API resolves it to **users linked to that unit**. When it refers to a unit on the **audit object** side, it resolves to **audit objects linked to that unit**.

Prefer this endpoint and unit-based semantics for new integrations.

### Example Request

```http
GET /company-structure-units
Host: api-external.monitorqa.com
X-API-KEY: abcdef12345
```

## Response

**Success Response**

```http
HTTP/1.1 200 OK
Content-Type: application/json

[
  {
    "id": "123456gh-ijkl-789a-bcde-f12345678901",
    "name": "Safety Inspectors"
  },
  {
    "id": "234567hi-jklm-890a-bcde-f12345678902",
    "name": "Quality Assurance Team"
  },
  {
    "id": "345678ij-klmn-901a-bcde-f12345678903",
    "name": "Maintenance Supervisors"
  }
]
```

### Response Fields

| Field | Type | Description |
|-------|------|-------------|
| `id` | uuid | Company structure unit identifier |
| `name` | string | Display name of the unit |

For errors responses, see the [response status codes documentation](#/response-status-codes).
