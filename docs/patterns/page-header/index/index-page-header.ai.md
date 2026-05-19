# Index Page Header — AI Specification

## Component
PageHeader (Index)

---

## Input

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

## Composition Rules

- Always render `title`

- Render `metadata` if provided
- Render `description` only if `metadata` is not provided

- Render `headerNav` only if more than one dataset exists

- Render `action` only if a primary action exists

- Render `documentationButton` if `true`

---

## Layout Rules

Top row:
- Left area:
  - Title
  - Description OR metadata

- Right area:
  - Documentation Button (if present)
  - Action (if present)

Bottom row:
- Header Nav (if present)

Rules:
- Header Nav always appears below the top row
- Header Nav spans the full header width
- Header Nav is not part of the left content area

---

## Constraints

- Do not render overflow (“…”) menus
- Do not render search
- Do not render filters
- Do not render sorting
- Do not render breadcrumbs
- Do not render item-level actions

---

## Decision Rules

- If `metadata` exists → use it
- Else if `description` exists → use it

- If `headerNav.length > 1` → render Header Nav
- Else → do not render Header Nav

- If multiple primary actions exist → use `action.type = "button-group"`
- Else → use `action.type = "button"`

- If `action` is not defined → do not render it

- If `documentationButton = true` → render Documentation Button
- If `documentationButton = false` or undefined → do not render it

---

## Variants

### Without Header Nav
- No `headerNav` field

### With Header Nav
- `headerNav` required
- Active item controls content below the header

---

## Example — Storage

{
  "title": "Storage",
  "metadata": "3 buckets and 39 tables",
  "headerNav": [
    { "label": "Tables & Buckets", "value": "tables" },
    { "label": "Files", "value": "files" }
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
  "metadata": "123 jobs",
  "documentationButton": true
}