---
category: 14. Company
categoryOrder: 14
url_path: '/company'
title: 'Update company'
type: 'PUT'
order: 7
layout: null
---

Update company information including name, usage purpose, and time zone settings. This endpoint allows modification of company profile details.

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
| `usagePurpose` | number | Yes | The primary usage purpose for the company. Must be a valid enum value. Valid values: `0` (Locations), `1` (Stores), `2` (Sites), `3` (Machines), `4` (Plants), `5` (Vehicles), `6` (Other), `7` (Processes) |
| `usagePurposeObjectName` | string | Conditional | Required when `usagePurpose` is `6` (Other). Custom name for the audit object type |
| `ianaTimeZone` | string | Yes | IANA time zone identifier (e.g., "America/New_York", "Europe/London") |

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

### Example Request

```http
PUT /company
Host: api-external.monitorqa.com
X-API-KEY: abcdef12345
Content-Type: application/json

{
  "companyName": "Example Company",
  "usagePurpose": 0,
  "ianaTimeZone": "America/New_York"
}
```

### Example Request (Other Usage Purpose)

```http
PUT /company
Host: api-external.monitorqa.com
X-API-KEY: abcdef12345
Content-Type: application/json

{
  "companyName": "Example Company",
  "usagePurpose": 6,
  "usagePurposeObjectName": "Facility",
  "ianaTimeZone": "America/Los_Angeles"
}
```

## Response

**Success Response**

```http
HTTP/1.1 200 OK
```

Empty response body indicates successful company update.

For errors responses, see the [response status codes documentation](#/response-status-codes).

