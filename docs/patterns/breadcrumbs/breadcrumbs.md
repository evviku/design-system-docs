# Breadcrumbs

## Overview
Breadcrumbs display the hierarchical path to the current entity and allow navigation to parent levels.

They are mandatory in the Detail Page Header.

---

## Anatomy

- Breadcrumb item (label)
- Separator (e.g. `>` or `/`)
- Optional dropdown trigger (chevron icon)

---

## Structure

Breadcrumbs consist of a sequence of items:

```txt
Storage > Bucket name > Table nameEach item represents one level in the hierarchy.

Behavior
Navigation
* All items except the last are links
* The last item represents the current entity and is not a link

Dropdown
Some breadcrumb items can include a dropdown.
Use dropdown when:
* the level contains multiple sibling entities
* users may need to quickly switch context within the same level

Dropdown trigger
* Dropdown is triggered by a separate icon (e.g. chevron)
* The label itself remains a navigation link (if not the last item)
Rules:
* Do not combine navigation and dropdown into a single click target
* Label click = navigation
* Icon click = dropdown

Dropdown content
Dropdown contains: list of sibling entities (e.g. buckets, tables)
Rules:
* Current entity should be highlighted
* Items navigate to selected entity
* List should be scrollable if long

Rules
* Breadcrumbs are always visible on detail pages
* Use real entity names (not generic labels)
* The last item is not clickable
* Keep hierarchy depth reasonable (max 3–4 levels)
* Do not duplicate full sidebar structure
* Use dropdown only when it adds real value
* Do not apply dropdown to all levels by default

Decision rules
* If level has multiple sibling entities → allow dropdown
* If quick switching is useful → use dropdown
* Else → render as simple link

Visual rules
* Items are displayed inline with separators
* Current item has highest emphasis
* Parent items have lower emphasis
* Dropdown trigger is visually attached to the item
* Dropdown trigger must not cause layout shift

Notes
* Breadcrumbs are navigation, not actions
* Entity-level actions belong to overflow menu (“…”) in the header
* Dropdown is used for navigation only, not for actions
