---
category: 3. Schedules
url_path: '/schedules/{scheduleId}'
title: 'Update schedule'
type: 'PUT'
order: 7
layout: null
---

Update an existing schedule's configuration, including audit objects, assignments, and recurrence patterns. This endpoint allows you to modify all aspects of a schedule except its template.

## Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| scheduleId | string | Yes | The unique identifier of the schedule to update |
| auditObjectIds | array[string] | Conditional | Array of audit object IDs (required if auditObjectGroupIds not provided) |
| auditObjectGroupIds | array[string] | Conditional | Array of audit object group IDs (required if auditObjectIds not provided) |
| name | string | Yes | Display name for the schedule |
| auditorHint | string | No | Hint text visible to auditors during the audit (max 2000 characters) |
| assigneesIds | array[string] | No | Array of user IDs to assign the generated audits to |
| repeatPattern | integer | Yes | Schedule repeat pattern (0=One-time, 1=Daily, 2=Multiple Weeks, 3=Monthly, 4=Weekly) |
| repeat | object | Yes | Repeat configuration options (varies by repeatPattern) |
| active | boolean | No | Schedule status (defaults to `true`, ignored for one-time schedules) |
| startFromDate | string | No | UTC date when schedule should start (format: `yyyy-MM-ddTHH:mm:ss.fffZ`, ignored for one-time) |
| stopByDate | string | No | UTC date after which schedule should stop (format: `yyyy-MM-ddTHH:mm:ss.fffZ`, ignored for one-time) |

## Repeat Pattern Options

### One-time (repeatPattern: 0)
```json
{
  "startDate": "2024-02-01T08:00:00.000Z",
  "endDate": "2024-02-15T17:00:00.000Z"
}
```

### Daily (repeatPattern: 1)
```json
{
  "repeatEvery": 3
}
```

### Multiple Weeks (repeatPattern: 2)
```json
{
  "repeatEvery": 2,
  "startDay": 1,
  "duration": 5
}
```

### Monthly (repeatPattern: 3)
```json
{
  "repeatEvery": 1,
  "startRule": {
    "type": 0,
    "day": 15
  },
  "endRule": {
    "type": 1,
    "days": 20
  }
}
```

**Note:** The first audit period begins at the closest date (based on the start rule) to the schedule creation date. For monthly schedules with Type 1 (StartOfMonth), the first period's cycle month is always the closest month after (or on) the schedule creation date - if created after the 1st, the cycle starts in the next month.

**First Period Examples:**
- **Type 0 with day: 15**: Schedule created on January 20 → first audit starts on February 15. Created on January 5 → first audit starts on January 15.
- **Type 1 with cycleMonthStart: 1, repeatEvery: 3**: Created on January 15 → first period cycle starts in February (month after creation, becomes month 1 of cycle), audit starts February 1. Created on January 1 → first period cycle starts in January (creation month, month 1 of cycle), audit starts January 1. Created on March 10 → first period cycle starts in April (month after creation, month 1 of cycle), audit starts April 1.

**StartRule types:**

The start rule determines when each audit period begins.

- **Type 0 (DayOfMonth)** - Start on a specific day of each scheduled month:
```json
{
  "type": 0,
  "day": 15
}
```
  - The `day` property (1-31) specifies which day of the month to start
  - If the month doesn't have that day (e.g., day 31 in February), the system uses the last day of that month
  - Handles leap years automatically (e.g., day 29 = Feb 29 in leap years, Feb 28 otherwise)
  - First period example: Schedule created on Jan 20 with `day: 15` → first audit starts on Feb 15

- **Type 1 (StartOfMonth)** - Start at the beginning of a specific month within the repeat cycle:
```json
{
  "type": 1,
  "cycleMonthStart": 1
}
```
  - The `cycleMonthStart` property (1, 2, 3...) specifies which month within the `repeatEvery` cycle to start
  - The audit always starts on the 1st day of the selected month in each cycle
  - Example: `cycleMonthStart: 1` with `repeatEvery: 3` starts on Jan 1, Apr 1, Jul 1, Oct 1
  - First period example: Schedule created on Jan 15 with `cycleMonthStart: 1` and `repeatEvery: 3` → first audit starts on Apr 1

**EndRule types:**

The end rule determines when each audit period ends. In all cases, if the calculated end date would overlap with the next audit's start date, the system automatically adjusts it to end one day before the next audit starts to prevent overlaps.

- **Type 0 (EndOfMonth)** - End at the end of a specific month within the cycle:
```json
{
  "type": 0,
  "cycleMonthEnd": 1
}
```
  - The `cycleMonthEnd` property (1, 2, 3...) specifies which month within the cycle to end
  - `cycleMonthEnd: 1` = end of same month as start, `2` = end of second month, etc.

- **Type 1 (AfterDays)** - End after a fixed number of days from the audit start:
```json
{
  "type": 1,
  "days": 20
}
```
  - The `days` property specifies how many days after the start date the audit ends
  - Example: Start on Jan 15 with `days: 20` ends on Feb 4

- **Type 2 (AfterWeeks)** - End after a fixed number of weeks from the audit start:
```json
{
  "type": 2,
  "weeks": 3
}
```
  - The `weeks` property specifies how many weeks after the start date the audit ends
  - Example: Start on Jan 15 with `weeks: 3` ends on Feb 5 (21 days later)

- **Type 3 (BeforeNextStarts)** - End one day before the next audit begins:
```json
{
  "type": 3
}
```
  - No additional properties needed
  - Automatically ends one day before the next scheduled audit starts, ensuring no overlap

**Complete Monthly Examples:**

Example with DayOfMonth start and AfterDays end:
```json
{
  "repeatEvery": 1,
  "startRule": {
    "type": 0,
    "day": 15
  },
  "endRule": {
    "type": 1,
    "days": 20
  }
}
```

Example with StartOfMonth start and EndOfMonth end:
```json
{
  "repeatEvery": 3,
  "startRule": {
    "type": 1,
    "cycleMonthStart": 1
  },
  "endRule": {
    "type": 0,
    "cycleMonthEnd": 3
  }
}
```

Example with DayOfMonth start and BeforeNextStarts end:
```json
{
  "repeatEvery": 1,
  "startRule": {
    "type": 0,
    "day": 10
  },
  "endRule": {
    "type": 3
  }
}
```

### Weekly (repeatPattern: 4)
```json
{
  "daysOfWeek": [1, 3, 5],
  "repeatEvery": 2,
}
```

### Example Request

```http
PUT /schedules/456e7890-e89b-12d3-a456-426614174000
Host: api-external.monitorqa.com
X-API-KEY: abcdef12345
Content-Type: application/json

{
  "auditObjectIds": [
    "456e7890-e89b-12d3-a456-426614174000",
    "789e0123-e89b-12d3-a456-426614174000"
  ],
  "name": "Updated Daily Safety Check",
  "auditorHint": "Updated instructions: Focus on new safety protocols",
  "assigneesIds": [
    "abc12345-e89b-12d3-a456-426614174000",
    "def67890-e89b-12d3-a456-426614174000"
  ],
  "repeatPattern": 1,
  "repeat": {
    "repeatEvery": 2
  },
  "active": true,
  "startFromDate": "2024-02-01T08:00:00.000Z",
  "stopByDate": "2024-12-31T23:59:59.000Z"
}
```

## Response

**Success Response**

```http
HTTP/1.1 200 OK
```

Empty response body indicates successful schedule update.

For errors responses, see the [response status codes documentation](#/response-status-codes).
