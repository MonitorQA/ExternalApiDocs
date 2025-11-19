---
category: 8. Company Information
url_path: '/company'
title: 'Create company'
type: 'POST'
order: 3
layout: null
---

Create a new company account. This endpoint sets up a new organization with an initial company administrator. The authenticated user becomes the company administrator for the newly created company.

**Note:** To retrieve a list of available IANA time zones, use the [Get timezones](#/get-timezones) endpoint.

### Request Headers

| Header | Type | Required | Description |
|--------|------|----------|-------------|
| `X-API-KEY` | string | Yes | API authentication key |
| `Content-Type` | string | Yes | Must be `application/json` |

### Request Body Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `companyName` | string | Yes | The company name. Must be a valid company name format. |
| `companyAdmin` | object | Yes | Company administrator information |
| `companyAdmin.fullName` | string | Yes | Full name of the company administrator. Must be a valid user name format. |
| `companyAdmin.phone` | string | No | Phone number of the company administrator |
| `usagePurpose` | number | Yes | The primary usage purpose for the company. Valid values: `0` (Locations), `1` (Stores), `2` (Sites), `3` (Machines), `4` (Plants), `5` (Vehicles), `6` (Other), `7` (Processes) |
| `usagePurposeObjectName` | string | Conditional | Required when `usagePurpose` is `6` (Other). Custom name for the audit object type |
| `ianaTimeZone` | string | No | IANA time zone identifier (e.g., "America/New_York", "Europe/London") |

### Usage Purpose Values

| Value | Description |
|-------|-------------|
| `0` | Locations |
| `1` | Stores |
| `2` | Sites |
| `3` | Machines |
| `4` | Plants |
| `5` | Vehicles |
| `6` | Other |
| `7` | Processes |

### Example Request (Minimum Required Fields)

```http
POST /company
Host: api-external.monitorqa.com
X-API-KEY: abcdef12345
Content-Type: application/json

{
  "companyName": "Example Company",
  "companyAdmin": {
    "fullName": "Admin Name"
  },
  "usagePurpose": 0
}
```

### Example Request (All Fields)

```http
POST /company
Host: api-external.monitorqa.com
X-API-KEY: abcdef12345
Content-Type: application/json

{
  "companyName": "Example Company",
  "companyAdmin": {
    "fullName": "Admin Name",
    "phone": "+1-555-123-4567"
  },
  "usagePurpose": 0,
  "ianaTimeZone": "America/New_York"
}
```

### Example Request (Other Usage Purpose)

```http
POST /company
Host: api-external.monitorqa.com
X-API-KEY: abcdef12345
Content-Type: application/json

{
  "companyName": "Example Company",
  "companyAdmin": {
    "fullName": "Admin Name",
    "phone": "+1-555-123-4567"
  },
  "usagePurpose": 6,
  "usagePurposeObjectName": "Facility",
  "ianaTimeZone": "America/Los_Angeles"
}
```

## Response

**Success Response**

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "companyId": "456789jk-lmno-012b-cdef-123456789012"
}
```

### Response Fields

| Field | Type | Description |
|-------|------|-------------|
| `companyId` | uuid | The unique identifier of the newly created company |

The response contains the unique identifier of the newly created company.

For errors responses, see the [response status codes documentation](#/response-status-codes).

