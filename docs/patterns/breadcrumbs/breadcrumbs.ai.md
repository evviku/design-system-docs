# Breadcrumbs — AI Specification

## Component
Breadcrumbs

---

## Purpose

Represents hierarchical navigation within a section.

Helps users:
- understand current location
- navigate to parent levels

---

## Input

type BreadcrumbItem = {
  label: string
  href?: string

  dropdown?: Array<{
    label: string
    href: string
  }>
}

type Breadcrumbs = {
  items: BreadcrumbItem[]
}

---

## Rendering Rules

- Render items in a horizontal row
- Separate items with divider ("/" or chevron)

For each item:

### Default item
- If `href` exists → render as link
- If no `href` → render as static text

### Last item (current page)
- Always render as static text
- Never clickable

---

## Dropdown Behavior

- If `dropdown` exists:
  - Render item as dropdown trigger (not a link)
  - On click → open dropdown menu

### Important constraint
- Breadcrumb item cannot be both:
  - link (`href`)
  - dropdown trigger

---

## Dropdown Content

- First item MUST be:
  - link to the parent page (same level as breadcrumb item)

- Followed by:
  - hierarchical items (e.g. storage tree)

Example:

- Storage (breadcrumb)
  → dropdown:
    - "All Storage" (link to index page)
    - Bucket A
    - Bucket B

---

## Visibility Rules

- Show breadcrumbs only when:
  - page has a parent in the same section
  - hierarchy depth ≥ 2

- Do NOT show on:
  - top-level index pages
  - flat navigation pages

---

## Hierarchy Rules

- Maximum visible levels: 3–4
- If deeper:
  - collapse middle items into dropdown

---

## Interaction

- Clicking a breadcrumb navigates to that level
- Dropdown opens on click (not hover)

---

## Edge Cases

- Long labels should truncate
- Do not wrap to multiple lines
- Maintain single-line layout

---

## Anti-patterns

- Do not duplicate sidebar navigation
- Do not make last item clickable
- Do not combine link + dropdown on same item