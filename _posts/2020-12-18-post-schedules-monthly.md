---
category: 3. Schedules
url_path: '/schedules/monthly'
title: 'Create monthly schedule'
type: 'POST'
order: 6
layout: null
---

Create a monthly recurring schedule that generates audits at specified intervals on a particular day of the month. This endpoint enables setting up automated audit creation with flexible monthly recurrence patterns.

## Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| templateId | string | Yes | The unique identifier of the audit template to use |
| auditObjectIds | array[string] | Conditional | Array of audit object IDs (required if auditObjectGroupIds not provided) |
| auditObjectGroupIds | array[string] | Conditional | Array of audit object group IDs (required if auditObjectIds not provided) |
| name | string | Yes | Display name for the schedule |
| auditorHint | string | No | Hint text visible to auditors during the audit (max 2000 characters) |
| assigneesIds | array[string] | No | Array of user IDs to assign the generated audits to |
| repeatEvery | integer | Yes | Interval in months between audit creation |
| startRule | object | Yes | Rule to determine start of scheduling period |
| endRule | object | Yes | Rule to determine end of scheduling period |
| active | boolean | No | Schedule status (defaults to `true`) |
| startFromDate | string | No | UTC date when schedule should start (format: `yyyy-MM-ddTHH:mm:ss.fffZ`) |
| stopByDate | string | No | UTC date after which schedule should stop (format: `yyyy-MM-ddTHH:mm:ss.fffZ`) |


### Start rule description

The start rule determines when each audit period begins. **Note:** The first audit period begins at the closest date (based on the start rule) to the schedule creation date. For monthly schedules with Type 1 (StartOfMonth), the first period's cycle month is always the closest month after (or on) the schedule creation date - if created after the 1st, the cycle starts in the next month.

**First Period Examples:**
- **Type 0 with day: 15**: If the schedule is created on January 20, the first audit starts on February 15 (the next occurrence of day 15). If created on January 5, the first audit starts on January 15 (the upcoming occurrence in the same month).
- **Type 1 with cycleMonthStart: 1, repeatEvery: 3**: The first period's cycle month is the closest month after the creation date. If created in January, the first month of the cycle is February (the month after creation). For example, created on January 15 with cycleMonthStart: 1 and repeatEvery: 3 - the first cycle starts in February (month 1), March (month 2), April (month 3), so the first audit starts on February 1 (month 1 of that cycle).

There are 2 types of start rule:
- **Type 0 (DayOfMonth)** - Start on a specific day of each scheduled month
- **Type 1 (StartOfMonth)** - Start at the beginning of a specific month within the repeat cycle
```json
{
  "type": 0,
  "day": number,
}
```

or 

```json
{
  "type": 1,
  "cycleMonthStart": number
}
```

#### Type 0 (DayOfMonth) - Specific Day of Month

When `type` is `0`, the audit starts on a fixed day of each scheduled month. The `day` property must be greater than 0 and in the range 1-31, specifying which day of the month to start the audit.

**How it works:**
- Each scheduled audit begins on the specified day of the month
- If the month doesn't have that day (e.g., day 31 in February), the system automatically uses the last day of that month
- Leap year handling: Day 29 in February becomes Feb 29 in leap years and Feb 28 in non-leap years

**Examples:**
- `{ "type": 0, "day": 15 }` - Audit starts on the 15th of each scheduled month (e.g., Jan 15, Feb 15, Mar 15)
- `{ "type": 0, "day": 1 }` - Audit starts on the 1st of each scheduled month
- `{ "type": 0, "day": 31 }` - Audit starts on the 31st (or last day if month has fewer days). February becomes Feb 29 in leap years, Feb 28 otherwise
- `{ "type": 0, "day": 29 }` - Handles leap years: Feb 29 in leap years, Feb 28 in non-leap years

**First Period Example:**
- Schedule created on January 20 with `{ "type": 0, "day": 15 }` - First audit starts on February 15 (next occurrence)
- Schedule created on January 5 with `{ "type": 0, "day": 15 }` - First audit starts on January 15 (upcoming in same month)

#### Type 1 (StartOfMonth) - Beginning of Month in Cycle

When `type` is `1`, the audit starts at the beginning (1st day) of a specific month within the repeat cycle. The `cycleMonthStart` property must be greater than 0 and specifies which month within the `repeatEvery` cycle should start the audit (1, 2, 3...).

**How it works:**
- Each repeat cycle contains `repeatEvery` months
- `cycleMonthStart` indicates the position within that cycle (1 = first month, 2 = second month, etc.)
- The audit always starts on the 1st day of the selected month in each cycle
- The first period's cycle month is always the closest month after (or on) the schedule creation date. If created after the 1st of a month, the cycle starts in the next month. If created on the 1st, the cycle may start in the current month.

**Examples:**
- `{ "type": 1, "cycleMonthStart": 1 }` with `repeatEvery: 3` - Starts on the 1st day of the first month in each 3-month cycle (e.g., Jan 1, Apr 1, Jul 1, Oct 1)
- `{ "type": 1, "cycleMonthStart": 2 }` with `repeatEvery: 3` - Starts on the 1st day of the second month in each 3-month cycle (e.g., Feb 1, May 1, Aug 1, Nov 1)
- `{ "type": 1, "cycleMonthStart": 1 }` with `repeatEvery: 1` - Starts on the 1st day of every month

**First Period Example:**
- Schedule created on January 15 with `{ "type": 1, "cycleMonthStart": 1 }` and `repeatEvery: 3` - First period cycle starts in February (the month after creation, which becomes month 1 of the cycle), first audit starts on February 1
- Schedule created on January 1 with `{ "type": 1, "cycleMonthStart": 1 }` and `repeatEvery: 3` - First period cycle starts in January (creation month, month 1 of cycle), first audit starts on January 1
- Schedule created on March 10 with `{ "type": 1, "cycleMonthStart": 1 }` and `repeatEvery: 3` - First period cycle starts in April (the month after creation, month 1 of cycle), first audit starts on April 1
- Schedule created on February 5 with `{ "type": 1, "cycleMonthStart": 2 }` and `repeatEvery: 3` - First period cycle starts in March (the month after creation, month 1 of cycle), first audit starts on April 1 (month 2 of that cycle)

### End rule description

The end rule determines when each audit period ends. There are 4 types of end rule:
- **Type 0 (EndOfMonth)** - End at the end of a specific month within the cycle
- **Type 1 (AfterDays)** - End after a fixed number of days from the audit start
- **Type 2 (AfterWeeks)** - End after a fixed number of weeks from the audit start
- **Type 3 (BeforeNextStarts)** - End one day before the next audit begins

**Important:** In all cases, if the calculated end date would overlap with the next audit's start date, the system automatically adjusts it to end one day before the next audit starts to prevent overlaps.
```json
{
  "type": 0,
  "cycleMonthEnd": number
}
```

or

```json
{
  "type": 1,
  "days": number
}
```

or

```json
{
  "type": 2,
  "weeks": number
}
```

or

```json
{
  "type": 3
}
```

#### Type 0 (EndOfMonth) - End at End of Month in Cycle

When `type` is `0`, the audit ends at the end of a specific month within the repeat cycle. The `cycleMonthEnd` property must be greater than 0 and specifies which month within the cycle the audit should end (1, 2, 3...).

**How it works:**
- `cycleMonthEnd: 1` means the audit ends at the end of the same month it started
- `cycleMonthEnd: 2` means the audit ends at the end of the second month in the cycle
- The end date is the last day of the specified month at end of day (23:59:59)

**Example:**
- `{ "type": 0, "cycleMonthEnd": 1 }` with start on Jan 15 - Audit ends on Jan 31
- `{ "type": 0, "cycleMonthEnd": 2 }` with start on Jan 15, `repeatEvery: 3` - Audit ends on Feb 28/29

#### Type 1 (AfterDays) - End After N Days

When `type` is `1`, the audit ends a fixed number of days after it starts. The `days` property must be greater than 0 and specifies how many days the audit period lasts.

**How it works:**
- The end date is calculated by adding `days` to the audit start date
- If this would overlap with the next audit, it's automatically adjusted to end one day before the next audit starts

**Example:**
- `{ "type": 1, "days": 20 }` with start on Jan 15 - Audit ends on Feb 4 (Jan 15 + 20 days)

#### Type 2 (AfterWeeks) - End After N Weeks

When `type` is `2`, the audit ends a fixed number of weeks after it starts. The `weeks` property must be greater than 0 and specifies how many weeks the audit period lasts.

**How it works:**
- The end date is calculated by adding `weeks * 7` days to the audit start date
- If this would overlap with the next audit, it's automatically adjusted to end one day before the next audit starts

**Example:**
- `{ "type": 2, "weeks": 3 }` with start on Jan 15 - Audit ends on Feb 5 (Jan 15 + 21 days)

#### Type 3 (BeforeNextStarts) - End Before Next Audit

When `type` is `3`, the audit automatically ends one day before the next scheduled audit begins. This ensures no overlap between consecutive audits.

**How it works:**
- No additional properties are needed
- The system calculates when the next audit will start based on `repeatEvery` and the start rule
- The current audit ends the day before that next start date

**Example:**
- With `repeatEvery: 1` and start on Jan 15 - Next audit starts Feb 15, so current audit ends Feb 14


### Example Request

```http
POST /schedules/monthly
Host: api-external.monitorqa.com
X-API-KEY: abcdef12345
Content-Type: application/json

{
  "templateId": "123e4567-e89b-12d3-a456-426614174000",
  "auditObjectIds": [
    "456e7890-e89b-12d3-a456-426614174000",
    "789e0123-e89b-12d3-a456-426614174000"
  ],
  "name": "Monthly Compliance Review",
  "auditorHint": "Review all compliance documentation and procedures",
  "assigneesIds": [
    "abc12345-e89b-12d3-a456-426614174000",
    "def67890-e89b-12d3-a456-426614174000"
  ],
  "repeatEvery": 1,
  "startRule": {
    "type": 0,
    "day": 29,
  },
  "endRule": {
    "type": 1,
    "days": 3
  },
  "active": true,
  "startFromDate": "2024-01-01T08:00:00.000Z",
  "stopByDate": "2024-12-31T23:59:59.000Z"
}
```

## Response

**Success Response**

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "id": "456789op-qrst-567g-hijk-678901234570"
}
```

For errors responses, see the [response status codes documentation](#/response-status-codes).
