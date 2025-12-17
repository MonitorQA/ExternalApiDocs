---
category: Time zones
categoryOrder: 15
url_path: '/timezones'
title: 'Get timezones'
type: 'GET'
order: 8
layout: null
---

Retrieve a list of all available IANA time zones. The time zones are ordered by their UTC offset at the current time, with the most negative offsets (earliest time zones) appearing first.

### Request Headers

| Header | Type | Required | Description |
|--------|------|----------|-------------|
| `X-API-KEY` | string | Yes | API authentication key |

### Example Request

```http
GET /timezones
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
    "ianaName": "Pacific/Midway",
    "text": "Pacific/Midway"
  },
  {
    "ianaName": "America/Adak",
    "text": "America/Adak"
  },
  {
    "ianaName": "America/Anchorage",
    "text": "America/Anchorage"
  },
  {
    "ianaName": "America/Los_Angeles",
    "text": "America/Los Angeles"
  },
  {
    "ianaName": "America/New_York",
    "text": "America/New York"
  },
  {
    "ianaName": "Europe/London",
    "text": "Europe/London"
  }
]
```

### Response Fields

| Field | Type | Description |
|-------|------|-------------|
| `ianaName` | string | The IANA time zone identifier (e.g., "America/New_York") |
| `text` | string | Human-readable time zone name with underscores replaced by spaces |

The time zones are ordered by UTC offset (most negative to most positive) at the time of the request.

For errors responses, see the [response status codes documentation](#/response-status-codes).

