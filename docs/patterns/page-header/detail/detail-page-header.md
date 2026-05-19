# Detail Page Header

## Overview
Detail Page Header is used on entity detail pages. It provides context about the current entity and exposes entity-level actions.

It always includes breadcrumbs and a title. It may include description, badges, actions, and tabs.

---

## Structure

The Detail Page Header consists of three main rows:

1. Breadcrumbs row  
2. Top row  
3. Bottom row (optional)

---

### 1. Breadcrumbs row

Contains:
- Breadcrumbs (left)
- Overflow menu “…” (right)

Purpose:
- Shows navigation hierarchy
- Provides access to secondary and destructive actions

Overflow menu contains actions such as:
- Delete
- Copy
- Duplicate
- Debug mode
- Manage permissions
- Other non-primary actions

Rules:
- Breadcrumbs are mandatory on detail pages
- Breadcrumbs are always visible
- The last item (current entity) is not a link
- Parent items are links
- Use real entity names (not generic labels)
- Overflow menu is right-aligned
- Do not place primary actions here

---

### 2. Top row

The Top row contains two internal rows:

#### Main row

Contains:
- Icon / Avatar (optional)
- Title (Inline Editable Text – Title)
- Badges (optional)
- Actions (optional, right-aligned)

---

#### Actions

Actions are optional.

Rules:
- Maximum of 2 visible actions:
  - Primary action (required if actions are present)
  - Secondary action (optional)
- Primary action can be:
  - Button
  - Button group with dropdown
- Secondary action is used only when an action must be elevated and cannot be placed in the primary dropdown
- All other actions must be placed in the overflow menu in the breadcrumbs row

---

#### Badges

Badges communicate important state or metadata of the entity.

Examples:
- Active / Disabled
- Live / Stopped / Error
- Unbound
- Shared
- Read-only

Rules:
- Placed next to the title
- If there is not enough horizontal space:
  - Badges wrap to the next line under the title
- Keep badges short
- Do not use badges as actions

---

#### Description row

Contains:
- Description (Inline Editable Text – Description)

Rules:
- Description is optional
- Maximum width: 800px
- Uses Inline Editable Text pattern (Type: Description)
- In display:
  - Clamped to 2 lines
  - Fade applied if content overflows
- Editing behavior is defined in Inline Editable Text pattern
- Editing may increase header height

---

### 3. Bottom row (optional)

Contains:
- Header navigation (tabs)

Examples:
- Overview
- Events
- Settings

Rules:
- Used when the page has multiple sections
- Placed below the Top row
- Does not affect Title or Description behavior

---

## Behavior

### Title
- Uses Inline Editable Text (Type: Title)
- No layout shift when editing
- Full behavior is defined in Inline Editable Text pattern

---

### Description
- Uses Inline Editable Text (Type: Description)
- Editing may increase header height
- Full behavior is defined in Inline Editable Text pattern

---

## Layout rules

- Breadcrumbs row is always on top
- Title and badges align as a group
- Badges may wrap under the title
- Actions are right-aligned when present
- Description is placed below the title row
- Description max width is 800px
- Tabs are placed below the header content
- Title editing must not create layout shift

---

## Decision rules

- Always include breadcrumbs on detail pages
- Always include a title
- Actions are optional
- If actions are present:
  - Use one primary action
  - Add secondary only if necessary
- Use overflow menu for secondary and destructive actions
- Show badges only when they add value
- Use description for additional context when needed
- Use tabs only when content is divided into clear sections
- Do not place page-local actions (e.g. table actions) in the header

---

## Related patterns

- Inline Editable Text
- Breadcrumbs
- Button
- Button Group (with dropdown)
- Overflow Menu
- Badge
- Tabs