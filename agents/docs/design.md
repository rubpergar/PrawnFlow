# Design System

Reusable UI/design source of truth. Mark this file as `Not applicable` for projects without UI.

Document durable, reusable UI decisions here: visual principles, tokens, component rules, interaction states, accessibility rules, and responsive behavior. Do not document one-off screen details.

## Product Direction

- UI type:
- Audience:
- Tone:
- Density:
- Accessibility target:

## Visual Principles

List 3-6 principles that should guide reusable UI decisions.

| Principle | Meaning | Applies to |
|---|---|---|
| | | |
| | | |
| | | |

## Tokens

Document real tokens only after they exist. Use semantic names over raw visual descriptions so UI tasks can reuse meaning instead of inventing one-off values.

### Color Tokens

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

Expected shape when tokens are represented in config/code:

```yaml
tokens:
  color:
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
```

### Typography Tokens

| Token | Value | Usage |
|---|---|---|
| `font.body` | | Default body text |
| `font.heading` | | Headings and prominent labels |
| `text.xs` | | Metadata, captions |
| `text.sm` | | Secondary UI text |
| `text.md` | | Default UI/body text |
| `text.lg` | | Section headings |
| `text.xl` | | Page headings |
| `weight.regular` | | Default text |
| `weight.medium` | | Labels, controls |
| `weight.bold` | | Strong emphasis |
| `lineHeight.tight` | | Headings |
| `lineHeight.normal` | | Body/UI copy |

### Spacing Tokens

| Token | Value | Usage |
|---|---|---|
| `space.xs` | | Tight gaps |
| `space.sm` | | Compact component spacing |
| `space.md` | | Default spacing |
| `space.lg` | | Section spacing |
| `space.xl` | | Large layout spacing |
| `space.2xl` | | Page-level separation |

Expected shape when tokens are represented in config/code:

```yaml
tokens:
  spacing:
    xs:
    sm:
    md:
    lg:
    xl:
    2xl:
```

### Radius, Border, and Shadow Tokens

| Token | Value | Usage |
|---|---|---|
| `radius.sm` | | Small controls, tags |
| `radius.md` | | Inputs, buttons, cards |
| `radius.lg` | | Dialogs, large panels |
| `border.default` | | Standard border width/style |
| `shadow.sm` | | Subtle elevation |
| `shadow.md` | | Menus, cards, popovers |
| `shadow.lg` | | Dialogs, overlays |

Expected shape when tokens are represented in config/code:

```yaml
tokens:
  radius:
    sm:
    md:
    lg:
  border:
    default:
  shadow:
    sm:
    md:
    lg:
```

### Breakpoints

| Token | Value | Usage |
|---|---|---|
| `breakpoint.sm` | | Small/mobile layouts |
| `breakpoint.md` | | Tablet layouts |
| `breakpoint.lg` | | Desktop layouts |
| `breakpoint.xl` | | Wide desktop layouts |

### Layering and Motion

| Token | Value | Usage |
|---|---|---|
| `z.dropdown` | | Menus, popovers |
| `z.sticky` | | Sticky headers/actions |
| `z.modal` | | Dialog overlays |
| `z.toast` | | Notifications |
| `motion.fast` | | Micro-interactions |
| `motion.normal` | | Standard transitions |
| `motion.slow` | | Larger state changes |
| `motion.easing` | | Default easing curve |

## Interactive States

Define reusable behavior for common component states.

| State | Visual rule | Accessibility/behavior rule |
|---|---|---|
| Default | | |
| Hover | | Do not rely on hover-only affordances |
| Focus visible | | Must be visible for keyboard users |
| Active/pressed | | Should communicate action feedback |
| Disabled | | Must communicate unavailable state and avoid hidden tooltips as the only explanation |
| Loading | | Must prevent duplicate destructive/expensive actions when relevant |
| Error | | Must include text or structural cue, not color alone |
| Success | | Must include text or structural cue when it conveys meaning |
| Selected/current | | Must not rely on color alone |

## Accessibility Rules

Use project-specific accessibility rules here. Default target is WCAG 2.2 AA unless the project defines another target.

- Contrast:
- Keyboard operation:
- Visible focus:
- Labels and accessible names:
- Target size:
- Color-independent meaning:
- Reduced motion:
- Screen reader announcements:

## Responsive Rules

- Layout strategy:
- Mobile behavior:
- Tablet behavior:
- Desktop behavior:
- Maximum content width:
- Text line length:
- Data table behavior:
- Safe-area handling:
- Localization/text expansion:

## Dark Mode

- Supported: `yes | no | planned | not applicable`
- Theme source: `system | user setting | both | not applicable`
- Token strategy:
- Assets/icons strategy:
- Known exceptions:

If dark mode is supported, define light and dark values through semantic tokens instead of one-off component colors.

## Reusable Components

Document reusable components, variants, states, constraints, and notes. Do not document one-off screen details.

| Component | Variants | States | Constraints | Notes |
|---|---|---|---|---|
| Button | | | | |
| Input | | | | |
| Select | | | | |
| Textarea | | | | |
| Checkbox/Radio | | | | |
| Table | | | | |
| Card | | | | |
| Modal/Dialog | | | | |
| Alert/Notice | | | | |
| Badge/Tag | | | | |

## When to Update

Update this file when a reusable token, component variant, layout rule, accessibility rule, interaction convention, dark-mode rule, or microcopy pattern changes.

Do not update it for normal use of existing components, unique page content, or one-off visual details that should not become reusable project rules.

## Known Exceptions

| Exception | Reason | Scope |
|---|---|---|
