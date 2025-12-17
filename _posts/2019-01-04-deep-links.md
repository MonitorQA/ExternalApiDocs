---
category: General
categoryOrder: 1
url_path: '/deep-links'
title: 'Deep Links'
order: 1
layout: null
---

### Overview

Deep links provide direct navigation to specific sections and items within the MonitorQA mobile application. These URLs can be used in notifications, emails, or other integrations to guide users directly to relevant content.

### Supported Deep Links

The MonitorQA mobile application supports the following deep link patterns:

| Link Pattern | Description | Parameters |
|-------------|-------------|------------|
| `https://app.monitorqa.com/settings` | Open application settings | None |
| `https://app.monitorqa.com/audits/pending/{auditId}` | Open specific pending audit details | `auditId` - Unique audit identifier |
| `https://app.monitorqa.com/audits/archive` | Open completed audits list | None |
| `https://app.monitorqa.com/audits/archive/{auditId}` | Open specific completed audit details | `auditId` - Unique audit identifier |
| `https://app.monitorqa.com/actions/pending` | Open pending corrective actions list | None |
| `https://app.monitorqa.com/actions/pending/{actionId}` | Open specific pending corrective action details | `actionId` - Unique corrective action identifier |

### Usage Examples

```text
# Open settings page
https://app.monitorqa.com/settings

# Open specific pending audit
https://app.monitorqa.com/audits/pending/123e4567-e89b-12d3-a456-426614174000

# Open specific corrective action
https://app.monitorqa.com/actions/pending/987fcdeb-51a2-43d8-b654-321098765432
```

### Implementation Notes

- All deep links require the user to be authenticated in the mobile app
- Invalid or expired IDs will redirect to the appropriate list view
- Deep links work on both iOS and Android versions of the MonitorQA mobile app