---
category: 3. Schedules
url_path: '/schedules/{scheduleId}'
title: 'Get schedule details'
type: 'GET'
order: 2
layout: null
---

Retrieve detailed information about a specific schedule, including its configuration, repeat patterns, and assigned objects.

### Request Headers

| Header | Type | Required | Description |
|--------|------|----------|-------------|
| `X-API-KEY` | string | Yes | API authentication key |

### Path Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `scheduleId` | string | Yes | Unique identifier of the schedule |

### Example Request

```http
GET /schedules/{scheduleId}
Host: api-external.monitorqa.com
X-API-KEY: abcdef12345
```

## Response

**Success Response**

* **`id`** is schedule id.
* **`name`** is schedule name.
* **`active`** is schedule status - inactive schedule doesn't generate audits.
* **`stopByDate`** is schedule last active date. Schedule will be deactivated after this date and will not generate new audits.
* **`startFromDate`** is schedule activation date. Schedule will be activated at this date and will generate new audits.
* **`auditorHint`** is auditor hint visible during audit.
* **`template`** is information about template.
* **`assignees`** is information about users assigned to this schedule.
* **`auditObjects`** is information about audit objects assigned to this schedule.
* **`auditObjectGroups`** is information about audit object groups assigned to this schedule.
* **`repeatPattern`** is schedule repeat pattern.
* **`repeat`** is repeat options. Options vary depending on **`repeatPattern`** value.

### Repeat Patterns

| Pattern | Description |
|---------|-------------|
| `0` | One-time audit - produces one audit with no repeat |
| `1` | Daily audit - repeats daily with configurable interval |
| `2` | Multiple weeks audit - repeats per week with configurable interval and start day |
| `3` | Monthly audit - repeats per month with configurable interval and start day |
| `4` | Weekly audit - repeats on specific days of week |

**Repeat options**

One-time audit repeat options:

```json
{
  "startDate": "2025-07-31T15:30:00.000Z",
  "endDate": "2025-08-31T15:30:00.000Z"
}
```

Daily audit repeat options:

```json
{
  "repeatEvery": number, //value in range 1..10
}
```

Multiple weeks audit repeat options:

```json
{
  "repeatEvery": number, //value in range 1..10
  "startDay": DayOfWeek, //0 - Sun ... 6 - Sat
  "duration": number //value in range 1..repeatEvery*7
}
```

Monthly audit repeat options:

```json
{
  "repeatEvery": number, //value in range 1..10
  "startRule": object, // define schedule period start options
  "endRule": object // define schedule period end options
}
```

**Note:** The first audit period begins at the closest date (based on the start rule) to the schedule creation date. For monthly schedules with Type 1 (StartOfMonth), the first period's cycle month is always the closest month after (or on) the schedule creation date - if created after the 1st, the cycle starts in the next month.

**First Period Examples:**
- **Type 0 with day: 15**: Schedule created on January 20 → first audit starts on February 15 (next occurrence). Created on January 5 → first audit starts on January 15 (upcoming in same month).
- **Type 1 with cycleMonthStart: 1, repeatEvery: 3**: Created on January 15 → first period cycle starts in February (month after creation, becomes month 1 of cycle), audit starts February 1. Created on January 1 → first period cycle starts in January (creation month, month 1 of cycle), audit starts January 1. Created on March 10 → first period cycle starts in April (month after creation, month 1 of cycle), audit starts April 1.

**StartRule types:**

The start rule determines when each audit period begins. There are 2 types:

- **Type 0 (DayOfMonth)** - Start on a specific day of each scheduled month:
```json
{
  "type": 0,
  "day": number
}
```
  - The `day` property must be greater than 0 and in the range 1-31, specifying which day of the month to start the audit
  - Each scheduled audit begins on the specified day of the month
  - If the month doesn't have that day (e.g., day 31 in February), the system automatically uses the last day of that month
  - Handles leap years: Day 29 in February becomes Feb 29 in leap years and Feb 28 in non-leap years
  - Example: `{ "type": 0, "day": 15 }` - Audit starts on the 15th of each scheduled month (e.g., Jan 15, Feb 15, Mar 15)
  - First period: Schedule created on Jan 20 with `day: 15` → first audit starts on Feb 15. Created on Jan 5 → first audit starts on Jan 15

- **Type 1 (StartOfMonth)** - Start at the beginning of a specific month within the repeat cycle:
```json
{
  "type": 1,
  "cycleMonthStart": number
}
```
  - The `cycleMonthStart` property must be greater than 0 and specifies which month within the `repeatEvery` cycle should start the audit (1, 2, 3...)
  - The audit always starts on the 1st day of the selected month in each cycle
  - Each repeat cycle contains `repeatEvery` months, and `cycleMonthStart` indicates the position within that cycle (1 = first month, 2 = second month, etc.)
  - The first period's cycle month is always the closest month after (or on) the schedule creation date. If created after the 1st of a month, the cycle starts in the next month
  - Example: `{ "type": 1, "cycleMonthStart": 1 }` with `repeatEvery: 3` - Starts on the 1st day of the first month in each 3-month cycle (e.g., Jan 1, Apr 1, Jul 1, Oct 1)
  - First period: Created on January 15 with `cycleMonthStart: 1` and `repeatEvery: 3` → first period cycle starts in February (month after creation), audit starts Feb 1. Created on January 1 → first period cycle starts in January, audit starts Jan 1. Created on March 10 → first period cycle starts in April, audit starts Apr 1

**EndRule types:**

The end rule determines when each audit period ends. There are 4 types. **Important:** In all cases, if the calculated end date would overlap with the next audit's start date, the system automatically adjusts it to end one day before the next audit starts to prevent overlaps.

- **Type 0 (EndOfMonth)** - End at the end of a specific month within the cycle:
```json
{
  "type": 0,
  "cycleMonthEnd": number
}
```
  - The `cycleMonthEnd` property must be greater than 0 and specifies which month within the cycle the audit should end (1, 2, 3...)
  - `cycleMonthEnd: 1` means the audit ends at the end of the same month it started
  - `cycleMonthEnd: 2` means the audit ends at the end of the second month in the cycle
  - The end date is the last day of the specified month at end of day (23:59:59)

- **Type 1 (AfterDays)** - End after a fixed number of days from the audit start:
```json
{
  "type": 1,
  "days": number
}
```
  - The `days` property must be greater than 0 and specifies how many days after the start date the audit ends
  - The end date is calculated by adding `days` to the audit start date
  - If this would overlap with the next audit, it's automatically adjusted to end one day before the next audit starts
  - Example: `{ "type": 1, "days": 20 }` with start on Jan 15 - Audit ends on Feb 4 (Jan 15 + 20 days)

- **Type 2 (AfterWeeks)** - End after a fixed number of weeks from the audit start:
```json
{
  "type": 2,
  "weeks": number
}
```
  - The `weeks` property must be greater than 0 and specifies how many weeks after the start date the audit ends
  - The end date is calculated by adding `weeks * 7` days to the audit start date
  - If this would overlap with the next audit, it's automatically adjusted to end one day before the next audit starts
  - Example: `{ "type": 2, "weeks": 3 }` with start on Jan 15 - Audit ends on Feb 5 (Jan 15 + 21 days)

- **Type 3 (BeforeNextStarts)** - End one day before the next audit begins:
```json
{
  "type": 3
}
```
  - No additional properties are needed
  - The system calculates when the next audit will start based on `repeatEvery` and the start rule
  - The current audit ends the day before that next start date, ensuring no overlap between consecutive audits
  - Example: With `repeatEvery: 1` and start on Jan 15 - Next audit starts Feb 15, so current audit ends Feb 14

Weekly audits repeat options:

```json
{
  "daysOfWeek": DayOfWeek[], //0 - Sun ... 6 - Sat
  "repeatEvery":  number, //value in range 1..10
}
```

**Example**

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
   "id": string,
   "name": string,
   "active": boolean,
   "stopByDate": "2025-12-31T23:59:59.000Z",
   "startFromDate": "2025-01-01T00:00:00.000Z",
   "auditorHint": string,
   "template": {
      "id": string,
      "name": string
   },
   "assignees": [
      {
         "id": string,
         "name": string
      }
   ],
   "auditObjects": [
      {
         "id": string,
         "name": string
      }
   ],
   "auditObjectGroups": [
      {
         "id": string,
         "name": string
      }
   ],
   "repeatPattern": 1, //Daily audit
   "repeat": {      
      "repeatEvery": number
   }
}
```

For errors responses, see the [response status codes documentation](#/response-status-codes).
