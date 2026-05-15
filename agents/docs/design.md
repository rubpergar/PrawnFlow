# Design System

Reusable UI/design source of truth. Mark as `Not applicable` for projects without UI.

Document only durable, reusable UI decisions here. Do not document one-off screen details.

Validation: `npx @google/design.md lint agents/docs/design.md` (optional, requires Node.js).

---

```yaml
---
version: alpha
name: GambaDesk
colors:
  background: white
  surface: gray-50
  foreground: gray-900
  muted: gray-500
  border: gray-300
  primary: indigo-600
  secondary: gray-600
  success: green-600
  warning: yellow-500
  danger: red-600
  focus: indigo-500
typography:
  body:
    fontFamily: 'Inter, ui-sans-serif, system-ui, sans-serif'
    fontSize: 1rem
  heading:
    fontFamily: 'Inter, ui-sans-serif, system-ui, sans-serif'
    fontSize: 1.5rem
rounded:
  sm: 0.375rem
  md: 0.5rem
  lg: 0.75rem
spacing:
  xs: 0.5rem
  sm: 1rem
  md: 1.5rem
  lg: 2rem
components:
  button:
    backgroundColor: indigo-600
    textColor: white
    rounded: 0.5rem
  input:
    backgroundColor: white
    borderColor: gray-300
    rounded: 0.5rem
---
```

## Overview

- **UI type:** Dashboard web app
- **Audience:** Coworking customers (mobile-first) and administrators (desk-heavy)
- **Tone:** Professional, clean, trustworthy
- **Density:** Moderate
- **Accessibility target:** WCAG 2.2 AA (default)
- **Dark mode:** planned

### Visual Principles

| Principle | Meaning | Applies to |
|---|---|---|
| Clarity first | Content and actions are immediately understandable | Navigation, forms, data tables |
| Consistent spacing | Use Tailwind spacing scale; avoid arbitrary values | All layouts |
| Mobile-first responsive | Design for small screens first, enhance for larger | All views |
| Minimal visual noise | Reduce borders, shadows, and decorative elements | Cards, tables, forms |

## Colors

Uses Tailwind CSS default palette via `tailwind.config.js`. No custom color tokens.

- Dark mode strategy: planned (Tailwind `dark:` variant)
- Known exceptions: Breeze default views may use hardcoded colors

## Typography

Uses system font stack via Tailwind (`font-sans`).

| Token | Font | Size | Weight | Line height | Usage |
|---|---|---|---|---|---|
| `body` | Inter/system | 1rem (text-base) | 400 | 1.5 | Default body text |
| `heading` | Inter/system | 1.5rem (text-2xl) | 600 | 1.25 | Page headings |

## Layout

- Layout strategy: Blade layouts with sidebar/topnav for dashboard, centered cards for auth
- Max content width: `max-w-7xl` (80rem)
- Breakpoints: sm (640px) / md (768px) / lg (1024px) / xl (1280px)

## Components

### Interactive States

| State | Visual rule | Accessibility rule |
|---|---|---|
| Default | Tailwind default style | — |
| Hover | opacity-90 or underline | Do not rely on hover-only affordances |
| Focus | ring-2 ring-indigo-500 | Must be visible for keyboard users |
| Disabled | opacity-50 cursor-not-allowed | Must communicate unavailable state |
| Error | border-red-500 + text-red-600 | Must include text, not color alone |

### Component Catalog

| Component | Variants | States | Notes |
|---|---|---|---|
| Button | primary, secondary, danger, ghost, link | default, hover, focus, disabled | Based on Breeze default styles |
| Input | text, email, password, select, textarea | default, focus, error, disabled | Tailwind forms plugin |
| Card | default | — | White bg, rounded-lg, shadow-sm |
| Modal | confirmation, form | — | Tailwind transition utility classes |

## Do's and Don'ts

- **Update** when a reusable token, component variant, layout rule, or accessibility rule changes.
- **Do not update** for normal use of existing components or one-off visual details.

### Known Exceptions

| Exception | Reason | Scope |
|---|---|---|
| | | |
