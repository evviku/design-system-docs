# Detail Page Header — AI Specification

## Component
PageHeader (Detail)

---

## Input

type DetailPageHeader = {
  breadcrumbs: Array<{
    label: string
    href?: string
  }>

  title: string

  badges?: Array<{
    label: string
    variant?: "default" | "success" | "warning" | "error"
  }>

  description?: string

  canGenerateDescription?: boolean

  actions?: {
    primary: {
      label: string
      type: "button" | "button-group"
    }
    secondary?: {
      label: string
    }
  }

  overflowActions?: Array<{
    label: string
    type?: "default" | "destructive"
  }>

  headerNav?: Array<{
    label: string
    value: string
  }>
}

---

## Composition Rules

- Always render `breadcrumbs`
- Always render `title`
- Always render Description field

- Render `badges` if provided

- Render `actions` only if `primary` exists
- Render `actions.secondary` only if provided

- Render `overflowActions` in breadcrumbs row if provided

- Render `headerNav` only if more than one item exists

---

## Layout Rules

### Breadcrumbs row
- Left area:
  - Breadcrumbs

- Right area:
  - Overflow menu (if `overflowActions` exist)

---

### Top row

#### Main row

- Left area:
  - Title
  - Badges (if present)

- Right area:
  - Secondary action (if present)
  - Primary action

Rules:
- Maximum of 2 visible actions (primary + optional secondary)
- Primary action is rightmost

---

#### Description row

- Left area:
  - Description

Rules:
- Description is always rendered
- Description is placed below title
- Max width: 800px

---

### Bottom row

- Header Nav (if present)

Rules:
- Header Nav appears below Top row
- Header Nav spans full width

---

## Constraints

- Do not render search
- Do not render filters
- Do not render sorting
- Do not render item-level actions
- Do not render more than 2 visible actions (primary + optional secondary)

---

## Decision Rules

- Always render breadcrumbs
- Last breadcrumb item must not have `href`

- Always render title

- Always render Description field
- If `description` exists → render filled state
- If `description` is empty or undefined → render empty state

- If `canGenerateDescription = true` → show “Generate with Kai”
- If `canGenerateDescription = false` or undefined → do not show it

- If `badges` exist → render next to title
- If badges overflow → wrap under title

- If `actions.primary` exists → render actions
- If `actions.secondary` exists → render it next to primary
- If no `actions` → do not render action area

- If multiple primary actions exist → use `type = "button-group"`
- Else → use `type = "button"`

- If `overflowActions` exist → render “…” menu in breadcrumbs row
- Else → do not render overflow menu

- If `headerNav.length > 1` → render Header Nav
- Else → do not render Header Nav

---

## Variants

### Without Header Nav
- No `headerNav` field

### With Header Nav
- `headerNav` required
- Active item controls content below the header

---

## Example — Bucket Detail

{
  "breadcrumbs": [
    { "label": "Storage", "href": "/storage" },
    { "label": "Marketing bucket" }
  ],
  "title": "Marketing bucket",
  "badges": [
    { "label": "Active", "variant": "success" }
  ],
  "description": "Contains marketing datasets and transformation outputs.",
  "canGenerateDescription": true,
  "actions": {
    "primary": {
      "label": "Add table",
      "type": "button-group"
    }
  },
  "overflowActions": [
    { "label": "Copy" },
    { "label": "Delete", "type": "destructive" }
  ]
}

---

## Example — Empty Description

{
  "breadcrumbs": [
    { "label": "Data Apps", "href": "/data-apps" },
    { "label": "Sales dashboard" }
  ],
  "title": "Sales dashboard",
  "canGenerateDescription": true,
  "actions": {
    "primary": {
      "label": "Deploy",
      "type": "button"
    },
    "secondary": {
      "label": "Open editor"
    }
  },
  "overflowActions": [
    { "label": "Duplicate" },
    { "label": "Delete", "type": "destructive" }
  ]
}