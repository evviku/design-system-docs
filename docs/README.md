# Design System — AI-Driven Documentation

This repository contains a structured design system built for both humans and AI agents.

It defines UI patterns, behavior, and decision logic in a way that enables:
- designers to understand and evolve the system
- developers to implement it consistently
- AI (e.g. Claude) to generate UI aligned with the system

---

## Structure
/docs
/patterns
/[component-name]
component-name.md
component-name.ai.md
component-name.mapping.md (optional)

---

## File Types

- `.md` → human-readable documentation (UX reasoning, context)
- `.ai.md` → AI specification (structure, behavior, constraints)
- `.mapping.md` → mapping between page data and component props (only when needed)

---

## How to Use

### Designers
- Use `.md` files to understand patterns and intent
- Follow decision logic when designing new screens
- Keep patterns consistent across the product

---

### Developers
- Use `.ai.md` as the primary implementation source
- Use `.md` to understand context, intent, and edge cases
- Do not introduce custom variations outside defined patterns
- Respect behavior and constraints defined in specs

---

### AI (Claude, etc.)
- Locate the relevant pattern in `/patterns`
- Use `.ai.md` as the source of truth
- Apply decision logic before selecting a pattern
- Do not invent new UI patterns unless explicitly required

---

## Principles

- Patterns are reusable and consistent  
- Behavior is defined, not implied  
- Decisions are rule-based, not subjective  
- UI is composed, not custom-built per page  

---

## Anti-Goals

- No one-off UI solutions  
- No hidden logic inside pages  
- No mixing responsibilities (layout vs component vs data)  

---

## Current Scope

This is an evolving system. Not all patterns are defined yet.

Current patterns:
- Page Header (Index, Detail)
- Inline Editable Text
- Breadcrumbs

---

## Conventions

- Each component lives in its own folder  
- Naming must be consistent:
  - `component-name.md`
  - `component-name.ai.md`
- AI files must remain strict, predictable, and implementation-focused  

---

## Next Steps

- Expand pattern library  
- Introduce shared decision rules (when patterns start overlapping)  
- Add design tokens (colors, spacing)  
- Define page schema for AI-generated pages  

---

## Maintained By

Design system owned and evolved as part of product design.

---

## How AI Should Read This Repository

This repository is designed to be machine-readable. Follow these rules strictly.

---

### 1. Locate the Correct Pattern
- Start in `/docs/patterns`
- Identify the relevant component (e.g. `page-header`, `breadcrumbs`)
- Navigate to the component folder

---

### 2. Use `.ai.md` as Source of Truth
- Always prioritize `component-name.ai.md`
- This file defines:
  - structure
  - behavior
  - rendering rules
  - constraints

Do not rely on `.md` files for implementation logic.

---

### 3. Use `.md` for Context Only
- Use `component-name.md` to understand:
  - intent
  - UX reasoning
  - examples

Do not extract strict rules from this file.

---

### 4. Apply Decision Logic Before Use
- Evaluate:
  - when to use the component
  - when not to use it

Do not select components arbitrarily.

---

### 5. Use `.mapping.md` When Present
- Use mapping files to translate page data into component props
- Do not invent custom mappings

---

### 6. Do Not Invent New UI Patterns
- Use only patterns defined in `/patterns`
- If no suitable pattern exists:
  - explicitly state that a new pattern is required
  - do not create ad-hoc UI

---

### 7. Respect System Constraints
Do not:
- add extra UI elements  
- modify structure  
- introduce new interaction patterns  

Follow specifications exactly.

---

### 8. Compose UI from Patterns
- Build pages using existing components
- Avoid page-specific UI logic
- Prefer composition over customization

---

### 9. Be Predictable
- Use consistent naming  
- Follow existing patterns  
- Avoid creative interpretation  

---

### 10. When Unsure
Prefer:
- simpler patterns  
- existing solutions  

Avoid:
- overengineering  
- inventing behavior  