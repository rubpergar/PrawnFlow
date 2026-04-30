---
name: interface-design
description: Use only for UI/UX work: designing, implementing, improving, or reviewing visible product interfaces, responsive layouts, components, forms, navigation, dashboards, interaction states, and accessibility tied to UI. Use for greenfield UI, integration into existing design systems, explicit redesigns, and UI reviews. Do not use for backend-only, database-only, scripts, SEO audits, security review, brand identity-only work, image generation, or measured performance optimization.
---

# Interface Design

This is the single UI skill for the skeleton. It consolidates and replaces the former `ui-ux-pro-max`, `frontend-design`, `web-design-guidelines`, and `accessibility` skills to reduce overlap, token usage, and activation ambiguity.

Use this skill when a task changes how an interface looks, feels, moves, reads, responds, or is operated by users.

## Internal Modifications

Modified by: Thinc/PrawnFlow skeleton
Date: 2026-04-30
Purpose: Consolidated UI guidance into a selective, checklist-first internal workflow.
Distribution: Internal use only unless licenses are reviewed before redistribution.
Original source/license: see `agents/skills/README.md`.

## Core Directives

- Match the active mode: greenfield builds foundations; integration fits in; redesign changes intentionally; review critiques without editing.
- Preserve existing design systems, styling conventions, and component patterns unless the user explicitly asks to replace them.
- Ship usable UI: semantic HTML, keyboard support, visible focus, labels, contrast, responsive layout, and clear states are non-negotiable.
- Prefer tokens, reusable components, and existing CSS/styling patterns over one-off colors, dimensions, dependencies, or visual tricks.
- Make the smallest correct change; report broader redesign, accessibility, or consistency work as follow-up unless it blocks the primary flow.

## Quick Context Switch

- Greenfield: create minimal foundations.
- Integration: be invisible; imitate what exists.
- Redesign: break patterns with intent.
- Review: critique, do not touch.

## Scope

Use for:

- New or changed pages, views, layouts, components, forms, tables, cards, charts, navigation, modals, dashboards, landing pages, and admin screens.
- Visual polish, typography, spacing, color, hierarchy, motion, responsive behavior, and interaction states.
- Product UX decisions such as information hierarchy, flow clarity, empty states, loading states, error recovery, and primary actions.
- Accessibility work tied to UI: semantic HTML, labels, focus, keyboard operation, contrast, target size, screen reader names, reduced motion, and form errors.
- UI review before shipping, unless the user explicitly asks for a separate code review, security review, SEO audit, or measured performance audit.

Do not use for:

- Backend-only, database-only, infrastructure, scripts, or non-visual automation.
- Technical SEO audits; use the SEO skill.
- Exploitable security analysis; use the security skill.
- Measured web performance optimization; use the performance skill. This skill only covers basic UI performance hygiene.

## Operating Rules

- Read `agents/docs/design.md`, `AGENTS.md`, and relevant source-of-truth docs when reusable UI rules, tokens, components, product context, domain rules, or accessibility conventions may exist.
- Preserve existing design systems unless the user explicitly asks for redesign.
- Make the smallest correct UI change; avoid broad redesigns during feature work.
- Use semantic HTML and native controls before custom widgets.
- Respect detected styling conventions; do not mix Tailwind, CSS Modules, CSS-in-JS, design-system props, or plain CSS unless the project already does or the task requires it.
- Avoid new visual-effect dependencies unless explicitly allowed.
- Check desktop and mobile behavior for substantial UI changes.
- In existing products, prefer consistency over novelty.
- Preserve current visual language when adding, fixing, or extending a feature inside an existing product.

## Project Mode Detection

Before starting substantial UI work, determine the project mode:

1. Greenfield mode: use when there is no existing UI, no design system, no established components, or the user explicitly asks to build from scratch.
2. Integration mode: use by default when working inside an existing project, product, repository, codebase, design system, or established UI.
3. Redesign mode: use only when the user explicitly asks for a redesign, new visual direction, rebrand, visual overhaul, modernization, or replacement of existing patterns.
4. Review mode: use when the user asks to evaluate, audit, critique, or inspect UI without implementing changes.

Default to integration mode whenever an existing product or codebase is present. Do not silently redesign existing UI during integration mode.

## Mode Rules

### Greenfield Mode

- Define a minimal design foundation before implementing screens: layout system, spacing scale, type scale, color roles, component primitives, interaction states, and accessibility baseline.
- Create only the design system needed for the current product scope.
- Establish reusable components early when the same pattern appears more than once.
- Choose a coherent visual direction from product context, user risk, density, brand maturity, and usage frequency.
- Prioritize durable product UI over decorative novelty.

### Integration Mode

- Inspect existing nearby screens, components, tokens, CSS utilities, theme files, and layout conventions before creating new patterns.
- Reuse existing components, tokens, spacing, typography, radius, shadows, icons, and interaction states.
- Make the smallest UI change that fits the existing product.
- Do not introduce a new visual direction, component style, animation language, or layout system unless explicitly requested.
- If existing patterns are inconsistent, follow the dominant local pattern in the touched area and report the inconsistency separately.
- If no suitable existing component exists, create the smallest compatible local extension instead of a broad new system.

### Redesign Mode

- Identify what may change: visual direction, layout, information architecture, components, tokens, motion, density, or copy tone.
- Preserve product correctness, accessibility, and core user flows even while changing visual style.
- Prefer systematic redesign over isolated visual patches.
- State which existing conventions are being replaced and why.
- Keep migration impact visible: affected components, shared styles, and likely downstream screens.

### Review Mode

- Judge the UI against the active mode.
- In integration mode, flag inconsistency with the existing product as a real issue.
- In redesign mode, evaluate whether the new direction is coherent, accessible, and systematically applied.
- In greenfield mode, evaluate whether the foundation is reusable enough without becoming overbuilt.
- Prioritize findings over praise or redesign suggestions.
- Report issues by severity with file and line references when code is available.
- Use severity labels: blocking, major, minor, polish.
- Blocking means the primary flow, accessibility, data understanding, or user trust is materially impaired.
- Do not rewrite the UI unless the user asks for implementation.

## Decision Priority

When UI rules conflict, resolve them in this order:

1. User task success: the primary flow is understandable, usable, reversible where needed, and error-tolerant.
2. Accessibility: the interface is keyboard-operable, perceivable, labelled, focused correctly, and WCAG 2.2 AA by default.
3. Active project mode: greenfield creates a coherent minimal foundation; integration preserves existing product patterns; redesign applies the explicitly chosen new direction systematically.
4. Maintainability: reuse components, tokens, layout primitives, and naming conventions.
5. Performance hygiene: avoid layout shift, unnecessary dependencies, heavy assets, and expensive motion.
6. Visual polish: improve aesthetics only when the higher-priority criteria remain intact.

If a memorable design choice conflicts with the active mode or design system, prefer the active mode and design system. If the smallest change leaves a UX or accessibility defect in the touched area, fix the defect before closeout or explicitly report why it cannot be fixed in scope.

## Workflow

1. Clarify the interface goal, user context, and constraints only when the task is ambiguous.
2. Read available project context when the product type, users, domain, or reusable UI rules matter.
3. Identify the current visual language and component patterns before editing.
4. Determine the project mode: greenfield, integration, redesign, review, or review plus another mode when modifying UI and checking the result.
5. Choose one coherent direction using the design selection rules below.
6. Implement structure, responsive layout, states, accessibility, and visual polish together; do not treat accessibility as an afterthought.
7. Review against the checklist and red flags below before closeout.

## Design Direction

- Avoid generic AI UI: predictable centered hero blocks, timid purple gradients, arbitrary glassmorphism, emoji icons, and interchangeable card grids.
- In greenfield or redesign mode, make one memorable design choice when it supports the product context.
- In integration mode, do not add memorable visual choices unless they already fit the existing product language.
- Use typography intentionally: readable body text, strong hierarchy, controlled line length, and consistent type scale.
- Use color semantically: primary, secondary, surface, text, muted, success, warning, error, and focus states. Avoid raw one-off colors in components when tokens exist.
- Keep light and dark modes coherent when the project supports them; color tokens should respond to system/user preference rather than hard-coded one-off values.
- Use spacing as structure: group related items, separate unrelated sections, and keep touch targets comfortable.
- Use motion sparingly and meaningfully. Prefer transform and opacity; respect `prefers-reduced-motion`.

Choose the direction from context, not taste:

- Product type: marketing pages can be more expressive; dashboards, admin tools, checkout, auth, and settings should favor clarity and predictability.
- Information density: dense data needs restrained visuals, strong grouping, stable alignment, and scannable typography.
- User risk: high-risk actions, money, permissions, health, legal, or destructive flows require conservative interaction patterns and stronger confirmation/recovery.
- Brand maturity: if a design system exists, extend it; if not, create a minimal local pattern instead of inventing a broad system.
- Usage frequency: repeated daily workflows prioritize speed, keyboard support, density control, and low visual fatigue over novelty.

## Design Drift Control

During integration mode, treat the following as design drift:

- New colors outside tokens.
- New font sizes outside the existing scale.
- New radius, shadow, border, or spacing patterns.
- New button, input, card, or modal styles that duplicate existing components.
- New animation language.
- New icon style.
- New density model.
- New layout primitives where existing ones work.

Do not introduce design drift unless the user explicitly requested redesign or the existing system cannot support the task.

If an existing project has weak or inconsistent UI patterns, do not redesign globally by default. Use the best local pattern available in the touched area. If the task would benefit from broader normalization, report it as a separate redesign or design-system follow-up.

## UX Rules

- Each screen should have a clear purpose and one dominant primary action when applicable.
- Navigation must be predictable, reversible, and consistent with the product structure.
- Loading states should appear when feedback would otherwise feel delayed; use skeletons for content regions when useful.
- For user actions that mutate data, provide immediate feedback; use optimistic UI only when rollback, pending, failure, and resync states are clear.
- Empty states should explain what is missing and offer the next useful action.
- Error states should state the problem, where it happened, and how to recover.
- Destructive actions need clear separation, confirmation, or undo depending on risk.
- Forms need visible labels, helper text where useful, validation near the field, and focus on the first invalid field after submit.
- Tables and charts need readable labels, legends, units, sorting/filtering affordances when relevant, and must not rely on color alone.

## Accessibility Baseline

Target WCAG 2.2 AA for normal product UI unless the project defines another target.

Accessibility enforcement:

- If the touched UI violates keyboard operation, accessible names, visible focus, labels, or contrast AA, fix it before closeout.
- If a full fix is not feasible within scope, report the exact remaining issue, user impact, and recommended follow-up.
- Do not close UI work as complete when the primary path is unusable by keyboard or screen reader users.

- Use semantic landmarks, headings in order, native buttons/links/inputs, and labels associated with controls.
- Provide accessible names for icon-only buttons and meaningful alt text for informative images; decorative images use empty alt text.
- Keep normal text contrast at least 4.5:1, large text at least 3:1, and UI component boundaries/icons at least 3:1.
- Never remove visible keyboard focus. Use `:focus-visible` or equivalent project patterns.
- Ensure all interactive behavior works by keyboard and does not create keyboard traps.
- Keep touch/click targets at least 24x24 CSS px for WCAG AA and prefer 44x44 px for comfortable touch UI.
- Do not convey meaning through color alone; include text, icons, or structural cues.
- Respect reduced motion and avoid blocking interaction during animation.
- Manage focus for dialogs, drawers, popovers, route changes, and submit errors.
- Use `aria-live` or equivalent announcements for async status, form errors, and non-disruptive toasts when needed.

## Responsive Rules

- Design mobile-first, then expand to tablet and desktop.
- Avoid horizontal scroll on mobile unless it is an intentional data-table pattern with visible affordance.
- Prefer fluid containers, sensible max widths, and readable line lengths.
- Use `min-height: 100dvh` or equivalent over fragile `100vh` mobile layouts when relevant.
- Fixed headers, bottom bars, and overlays must account for safe areas and not obscure focused content.
- Keep primary content and actions reachable on small screens.
- Account for localization: allow text expansion, avoid fixed text containers, and preserve layout for longer labels, formatted numbers/dates, and RTL direction when the project supports right-to-left languages.

## UI Performance Hygiene

Use these checks during UI work, but use the performance skill for audits, budgets, metrics, or deep optimization.

- Reserve image/media dimensions to avoid layout shift.
- Prefer responsive images and modern formats when adding significant imagery.
- Lazy-load below-fold media and heavy non-critical UI.
- Avoid animating layout properties such as width, height, top, left, or expensive shadows.
- Avoid adding large client-side libraries for purely decorative UI.
- Keep custom fonts limited, use `font-display`, and avoid excessive font weights.

Performance red flags during UI work:

- New UI dependency for a simple component, icon, animation, or formatting task.
- More than one new UI dependency in the same task without explicit approval.
- Large unoptimized hero/media assets, missing dimensions on images, or intentional layout shifts.
- Animation that runs continuously, blocks input, or targets layout properties.
- Font additions with multiple families or many weights for a small UI change.

## Trade-Offs

Make trade-offs explicit when a UI choice has a meaningful cost:

- Performance vs aesthetics: preserve usability and loading stability over decorative assets or animation.
- Density vs legibility: choose density only when users need comparison/scanning and labels remain readable.
- Speed vs UX quality: small scope is preferred, but not at the cost of broken primary flows, missing states, or inaccessible controls.
- Consistency vs novelty: novelty belongs in isolated moments; repeated controls and flows should stay consistent.

If a trade-off is unresolved and affects behavior, accessibility, or user trust, make the safest reversible assumption, record it in the task plan, and ask only when proceeding would create material risk.

## Red Flags

Treat these as blocking unless the user explicitly accepts the trade-off:

- Primary interaction is not usable by keyboard.
- Focus is hidden, trapped, or obscured by sticky/fixed UI.
- Normal text contrast is below 4.5:1 or interactive boundaries/icons are below 3:1.
- Form fields rely on placeholders instead of labels.
- Error, success, required, selected, or disabled state is conveyed by color alone.
- Mobile layout has unintentional horizontal scroll, clipped controls, or unreachable primary actions.
- A destructive action has no confirmation, undo, or clear recovery path.
- More than three one-off colors, shadow styles, radius values, or font sizes are introduced outside existing tokens.
- New styling approach is introduced where the project already has a clear styling convention.
- New visual pattern duplicates an existing component without clear benefit; treat as blocking when it affects consistency, maintainability, or user recognition.

## Review Checklist

- The UI matches the existing product patterns or an explicitly chosen new direction.
- The visual hierarchy makes the primary content and action obvious.
- Layout works on mobile and desktop without overflow or clipped controls.
- Interactive states exist for hover, focus, active/pressed, disabled, loading, empty, error, and success where relevant.
- Keyboard users can reach and operate all controls.
- Screen reader names, labels, heading order, landmarks, and live regions are correct where relevant.
- Color contrast and non-color cues are sufficient.
- Motion is meaningful, performant, and reduced-motion safe.
- Forms show useful validation and recovery guidance.
- Images, fonts, and animations do not introduce obvious layout shift or avoidable weight.

## External Guideline Reviews

Do not fetch external web design guidelines by default. If the user explicitly asks for a guideline compliance review or pre-release UI audit, fetch the requested guideline source or the project-approved source and report findings with file and line references.
