# Index Page Header

## Overview
The Index Page Header provides context and primary actions for list-based pages (e.g. Components, Storage, Jobs). It establishes orientation, exposes key actions, and ensures consistency across all index views.

---

## Anatomy

### Required
- **Title**  
  Name of the section (e.g. Storage, Jobs, Components)

### Optional
- **Description / Metadata**
  - A single text field used for either:
    - contextual description (e.g. “Data shared between this project…”)
    - OR system metadata (e.g. “5 components and 35 configurations”)

- **Header Nav**
  - Horizontal navigation used to switch between related datasets within the same section
  - Example: Tables & Buckets / Files / Events

- **Action**
  - Main action for the page (e.g. New bucket, Add component)
  - Can be represented as:
    - Button
    - Button group (when multiple actions are available)

- **Documentation Button**
  - Icon button linking to documentation

---

## Usage

### Use this pattern for:
- All index (list) pages
- Pages representing a collection of entities
- Sections where users need to create, browse, or manage items

### Do NOT use for:
- Detail pages (use Detail Page Header)
- Dashboards
- Fullscreen tools (editors, builders)

---

## Behavior

- Header height is stable within expected content limits  
  - It does not shift dynamically due to loading or interaction  
  - It may expand if description wraps to multiple lines  

- Right-side actions are aligned and stable  
  - Action and Documentation Button do not shift based on content changes  

- Header Nav (if present)  
  - Switching updates content below the header only  
  - Does not change header structure  

- Description / Metadata  
  - Optional  
  - Must remain short and scannable  
  - Has a maximum width of **600px** to maintain readability  
  - Text wraps to the next line when exceeding available space  
  - No truncation or expand/collapse behavior  

- Documentation Button  
  - Always right-aligned within the actions area  
  - Can exist independently if no Action is present  

- Action  
  - Optional  
  - If not present, it is not rendered (no placeholder or empty space)  

---

## Decision Logic

### Description vs Metadata
- If metadata is available, use it  
- If metadata is not available, use description  
- Never display both  

---

### Header Nav
- Use Header Nav when:
  - The page contains multiple related datasets  
  - The datasets share context but differ in structure  

- Do not use Header Nav when:
  - There is only one dataset  
  - It would act as navigation to unrelated areas  

---

### Action
- Use Action when:
  - There is a clear primary action (create, add, share)  

- Use Button group when:
  - Multiple actions of similar importance exist  

- Do not use:
  - Overflow (“…”) menus  
  - Hidden or secondary action patterns  

---

### Documentation Button
- Use when:
  - The page requires explanation or onboarding  

- Keep it subtle:
  - Never a primary CTA  
  - Always icon-level importance  

---

## Rules
- Action is always creation-oriented, never navigation  
- Header must remain visually stable  
- Header Nav is the only navigation allowed inside the header  
- Do not use overflow (“…”) menus  
- Search does not belong in the header (use toolbar)  
- Keep description short and scannable  
- Do not overload the header with controls  

---

## Variants

### 1. Simple Header (no Header Nav)
Used for:
- Components  
- Jobs  
- Templates  
- Workspaces  

Structure:
- Title  
- Description or metadata  
- Actions  

---

### 2. Header with Header Nav
Used for:
- Storage  
- Transformations  
- Data Catalog  

Structure:
- Title  
- Description or metadata  
- Header Nav  
- Actions  

---

## Notes
- The header is not a control panel  
  - It provides context and entry points, not filtering or manipulation  

- The pattern is consistent across the product  
  - Even if some elements are not used  

- Prioritizes:
  - Clarity over density  
  - Consistency over flexibility  