# Index Page Header — Data Mapping

## Purpose

Defines what data is required to render the Index Page Header pattern.

This file can be used as a future contract for PageDefinition, API data, or static page configuration.

---

## Header Input

type IndexPageHeader = {
  title: string

  description?: string
  metadata?: string

  headerNav?: Array<{
    label: string
    value: string
  }>

  action?: {
    label: string
    type: "button" | "button-group"
  }

  documentationButton?: boolean
}

---

## Mapping Rules

- `title` is always required
- Use `metadata` when count or system summary is available
- Use `description` only when `metadata` is not available
- Use `headerNav` when the page contains multiple related datasets
- Use `action.type = "button"` for a single action
- Use `action.type = "button-group"` for multiple related actions
- Use `documentationButton = true` when the page links to documentation

---

## Constraints

Do not map these into the Index Page Header:

- Overflow (“…”) menus
- Search
- Filters
- Sorting
- Breadcrumbs
- Item-level actions
- Bulk actions
- Table settings
- Column customization

---

## Example — Storage

{
  "title": "Storage",
  "metadata": "3 buckets and 39 tables",
  "headerNav": [
    { "label": "Tables & Buckets", "value": "tables" },
    { "label": "Files", "value": "files" },
    { "label": "Data Streams", "value": "data-streams" },
    { "label": "Storage Jobs", "value": "storage-jobs" },
    { "label": "Events", "value": "events" }
  ],
  "action": {
    "label": "New bucket",
    "type": "button-group"
  },
  "documentationButton": true
}

---

## Example — Jobs

{
  "title": "Jobs",
  "description": "All execution records of components",
  "documentationButton": true
}