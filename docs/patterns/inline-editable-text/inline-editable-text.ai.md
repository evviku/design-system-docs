# Inline Editable Text — AI Specification

## Component
InlineEditableText

---

## Purpose

Allows user to edit text directly in place without leaving context.

Used for:
- titles
- descriptions
- names

---

## Input

type InlineEditableText = {
  value: string

  placeholder?: string

  isEditable?: boolean
  isMultiline?: boolean

  maxLength?: number
}

---

## States

The component has two states:

### View state
- Displays text
- If `value` is empty:
  - show `placeholder` (muted style)
- Styled as static content

### Edit state
- Displays editable variant of InlineEditableText
- Preserves layout, typography, and spacing
- Does NOT switch to external input/textarea component

---

## State Transitions

- Click (if `isEditable = true`) → View → Edit
- Blur → Edit → View (save)
- Enter → Edit → View (save, single-line only)
- Escape → Edit → View (cancel, revert value)

---

## Edit Behavior

### Focus
- Input is focused automatically on entering edit state
- Cursor is placed at the end of the text

### Value Handling
- Changes are applied immediately within component state
- Final value is committed on save

---

## Input Variant

- `isMultiline = true` → multiline edit variant
- otherwise → single-line edit variant

Note:
- Variants are internal to InlineEditableText
- Do NOT replace with generic input or textarea

---

## Validation

- Respect `maxLength` if defined
- Empty value handling is controlled externally

---

## Visual Rules

- No layout shift between states
- Editable state matches view state styling:
  - font
  - size
  - line height

---

## Interaction Constraints

- Only one InlineEditableText can be in edit state at a time (global rule)

---

## Edge Cases

- Long text:
  - wraps in multiline mode
  - truncates in single-line view state

- Empty value:
  - shows placeholder
  - remains editable

---

## Anti-patterns

- Do not replace component with generic input/textarea
- Do not move editing to modal or separate view
- Do not hide edit capability completely
- Do not rely only on hover if layout is unstable