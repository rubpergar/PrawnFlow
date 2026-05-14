# Design System

---

name: <project-name>
colors:
  background:
  surface:
  foreground:
  muted:
  border:
  primary:
  secondary:
  success:
  warning:
  danger:
  focus:
typography:
  body:
    fontFamily:
    fontSize:
  heading:
    fontFamily:
    fontSize:
  xs:
    fontFamily:
    fontSize:
  sm:
    fontFamily:
    fontSize:
  md:
    fontFamily:
    fontSize:
  lg:
    fontFamily:
    fontSize:
  xl:
    fontFamily:
    fontSize:
spacing:
  xs:
  sm:
  md:
  lg:
  xl:
  "2xl":
rounded:
  sm:
  md:
  lg:
components:
  button:
    backgroundColor: "{colors.primary}"
    textColor: "{colors.background}"
    rounded: "{rounded.md}"
  button-hover:
    backgroundColor:
  button-disabled:
    backgroundColor: "{colors.muted}"
  input:
    backgroundColor: "{colors.surface}"
    textColor: "{colors.foreground}"
    rounded: "{rounded.sm}"
  input-focus:
    borderColor: "{colors.focus}"
  card:
    backgroundColor: "{colors.surface}"
    rounded: "{rounded.md}"
  modal:
    backgroundColor: "{colors.surface}"
    rounded: "{rounded.lg}"
  select:
    backgroundColor: "{colors.surface}"
    textColor: "{colors.foreground}"
    rounded: "{rounded.sm}"
  table:
    backgroundColor:
  alert:
    backgroundColor:
  badge:
    backgroundColor:
    rounded: "{rounded.sm}"

---

Reusable UI/design source of truth. Mark this file as `Not applicable` for projects without UI.

Document durable, reusable UI decisions here: visual principles, tokens, component rules, interaction states, accessibility rules, and responsive behavior. Do not document one-off screen details.

Validate locally with `npx @google/design.md lint agents/docs/design.md` (requires Node.js; optional).

## Overview

- **UI type:**
- **Audience:**
- **Tone:**
- **Density:**
- **Accessibility target:** WCAG 2.2 AA unless otherwise specified
- **Dark mode supported:** `yes | no | planned | not applicable`
- **Dark mode source:** `system | user setting | both | not applicable`

### Visual Principles

List 3-6 principles that should guide reusable UI decisions.

| Principle | Meaning | Applies to |
|---|---|---|
| | | |
| | | |

## Colors

Explain the palette, token usage rules, and dark mode strategy.

| Token | Light value | Dark value | Usage |
|---|---|---|---|
| `background` | | | App/page background |
| `surface` | | | Cards, panels, elevated regions |
| `foreground` | | | Primary text/icons |
| `muted` | | | Secondary text, subtle UI |
| `border` | | | Dividers, outlines |
| `primary` | | | Primary actions and emphasis |
| `secondary` | | | Secondary actions and accents |
| `success` | | | Positive status |
| `warning` | | | Warning status |
| `danger` | | | Destructive/error status |
| `focus` | | | Focus rings and keyboard emphasis |

- **Dark mode token strategy:**
- **Dark mode assets/icons strategy:**
- **Known exceptions:**

## Typography

Describe the typographic hierarchy, font stack, and usage rules.

| Token | Font | Size | Weight | Line height | Usage |
|---|---|---|---|---|---|
| `body` | | | | | Default body text |
| `heading` | | | | | Headings and prominent labels |
| `xs` | | | | | Metadata, captions |
| `sm` | | | | | Secondary UI text |
| `md` | | | | | Default UI/body text |
| `lg` | | | | | Section headings |
| `xl` | | | | | Page headings |

## Layout

Define responsive behavior, breakpoints, and grid rules.

| Breakpoint | Value | Usage |
|---|---|---|
| `sm` | | Small/mobile layouts |
| `md` | | Tablet layouts |
| `lg` | | Desktop layouts |
| `xl` | | Wide desktop layouts |

- **Layout strategy:**
- **Mobile behavior:**
- **Tablet behavior:**
- **Desktop behavior:**
- **Maximum content width:**
- **Text line length:**
- **Data table behavior:**
- **Safe-area handling:**
- **Localization/text expansion:**

## Elevation & Depth

Define shadows, z-index layering, and motion.

| Shadow token | Value | Usage |
|---|---|---|
| `shadow.sm` | | Subtle elevation |
| `shadow.md` | | Menus, cards, popovers |
| `shadow.lg` | | Dialogs, overlays |

| Z-index token | Value | Usage |
|---|---|---|
| `z.dropdown` | | Menus, popovers |
| `z.sticky` | | Sticky headers/actions |
| `z.modal` | | Dialog overlays |
| `z.toast` | | Notifications |

| Motion token | Value | Usage |
|---|---|---|
| `motion.fast` | | Micro-interactions |
| `motion.normal` | | Standard transitions |
| `motion.slow` | | Larger state changes |
| `motion.easing` | | Default easing curve |

## Shapes

Define border radius and border styles.

| Token | Value | Usage |
|---|---|---|
| `radius.sm` | | Small controls, tags |
| `radius.md` | | Inputs, buttons, cards |
| `radius.lg` | | Dialogs, large panels |
| `border.default` | | Standard border width/style |

## Components

Define reusable component variants and their visual behavior.

### Interactive states

| State | Visual rule | Accessibility/behavior rule |
|---|---|---|
| Default | | |
| Hover | | Do not rely on hover-only affordances |
| Focus visible | | Must be visible for keyboard users |
| Active/pressed | | Should communicate action feedback |
| Disabled | | Must communicate unavailable state; avoid hidden tooltips as the only explanation |
| Loading | | Must prevent duplicate destructive/expensive actions when relevant |
| Error | | Must include text or structural cue, not color alone |
| Success | | Must include text or structural cue when it conveys meaning |
| Selected/current | | Must not rely on color alone |

### Component catalog

| Component | Variants | States | Constraints | Notes |
|---|---|---|---|---|
| Button | default, hover, disabled | | | |
| Input | default, focus | | | |
| Select | | | | |
| Textarea | | | | |
| Checkbox/Radio | | | | |
| Table | | | | |
| Card | | | | |
| Modal/Dialog | | | | |
| Alert/Notice | | | | |
| Badge/Tag | | | | |

## Do's and Don'ts

### Accessibility

- **Contrast:**
- **Keyboard operation:**
- **Visible focus:**
- **Labels and accessible names:**
- **Target size:**
- **Color-independent meaning:**
- **Reduced motion:**
- **Screen reader announcements:**

### File maintenance

**Update** when a reusable token, component variant, layout rule, accessibility rule, interaction convention, dark-mode rule, or microcopy pattern changes.

**Do not update** for normal use of existing components, unique page content, or one-off visual details that should not become reusable project rules.

### Known exceptions

| Exception | Reason | Scope |
|---|---|---|---|
| | | |
| | | |
| | | |
