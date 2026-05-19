# Inline Editable Text

## Overview
Inline Editable Text allows users to edit content directly in place without leaving the page context. It is used for titles and descriptions in detail page headers.

---

## Variants

### Type
- Title
- Description

### State
- Display
- Editing

### Content (Description only)
- Empty
- Filled

---

## Anatomy

### Display
- Text OR placeholder

### Editing
- Input (Title) or textarea (Description)

#### Description only (bottom row)
- Left: Generate with Kai
- Right: Save feedback (e.g. “Saved”)

---

## Usage

### Title
- Single-line content
- Always filled
- Used for primary entity name
- Lightweight inline editing

### Description
- Multi-line content
- Optional (can be empty)
- Supports richer editing
- May include AI generation and save feedback

---

## Behavior

### Enter editing
- Click on content

### Exit editing
- Click outside → collapse
- Esc → exit
- Changes are saved automatically

---

## Title behavior
- Single-line input
- No additional UI
- No layout shift between states

---

## Description behavior
- Multi-line textarea
- Can expand during editing
- Editing state may increase height

### Bottom row
- Left: Generate with Kai
- Right: Save feedback (e.g. “Saved”)

---

## States

### Empty state

#### Description (Display)
- Shows placeholder: “Add description”
- Shows inline action: “Generate with Kai”

#### Description (Editing)
- Empty textarea with placeholder
- Bottom row visible

---

### Filled state

#### Description (Display)
- Shows content
- Clamped to 2 lines
- Fade applied if content overflows

#### Description (Editing)
- Full content visible
- No clamping
- Editable

---

## Visual rules
- Editing should feel like an extension of display, not a separate component
- Title must not look like a form input
- Description may include additional UI in editing mode
- Fade is used instead of truncation

---

## Decision rules
- Use Title for short, required, single-line content
- Use Description for longer, optional, multi-line content
- Use inline editing when fast, in-context editing is needed
- Do not use for complex forms or validated inputs

---

## Notes
- Content differences (empty vs filled, short vs long) are not separate variants unless structure changes
- Description uses a content variant because empty state includes additional UI (Generate with Kai)
- Title does not support empty display state