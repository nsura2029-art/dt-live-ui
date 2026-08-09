# Design 1 — Editorial / Swiss · Design System (Shell freeze candidate)

> **Parity:** Feature structure must match Design 2 and Design 3. See `previews/README.md`.

## Direction
Editorial / Swiss clarity. Light mode only. Information-rich, tight hierarchy, restrained blue accent.

## Tokens

```css
:root {
  /* Colors */
  --color-bg: #fafafa;
  --color-surface: #ffffff;
  --color-surface-elevated: #ffffff;
  --color-border: #e4e4e7;
  --color-border-subtle: #f4f4f5;
  --color-text: #18181b;
  --color-text-muted: #71717a;
  --color-text-subtle: #a1a1aa;
  --color-primary: #18181b;
  --color-primary-foreground: #fafafa;
  --color-accent: #2563eb;
  --color-accent-muted: #dbeafe;

  /* Auth / brand gradients (additive) */
  --gradient-brand: linear-gradient(135deg, #1d4ed8 0%, #2563eb 45%, #7c3aed 100%);
  --gradient-login: linear-gradient(135deg, #eff6ff 0%, #e0e7ff 100%);
  --gradient-login-border: linear-gradient(135deg, #93c5fd 0%, #a5b4fc 100%);
  --gradient-signup: linear-gradient(135deg, #2563eb 0%, #4f46e5 50%, #7c3aed 100%);
  --gradient-signup-hover: linear-gradient(135deg, #1d4ed8 0%, #4338ca 50%, #6d28d9 100%);

  /* Typography */
  --font-sans: "Inter", ui-sans-serif, system-ui, -apple-system, sans-serif;
  --font-display: "Inter", ui-sans-serif, system-ui, sans-serif;
  --text-xs: 0.75rem;
  --text-sm: 0.875rem;
  --text-base: 1rem;
  --text-lg: 1.125rem;
  --text-xl: 1.25rem;
  --text-2xl: 1.5rem;
  --text-3xl: 1.875rem;
  --text-4xl: 2.25rem;
  --text-5xl: 3rem;
  --text-clock: clamp(2.5rem, 8vw, 4.5rem);

  /* Spacing */
  --space-1: 0.25rem;
  --space-2: 0.5rem;
  --space-3: 0.75rem;
  --space-4: 1rem;
  --space-5: 1.25rem;
  --space-6: 1.5rem;
  --space-8: 2rem;
  --space-10: 2.5rem;
  --space-12: 3rem;
  --space-16: 4rem;

  /* Radius */
  --radius-sm: 0.375rem;
  --radius-md: 0.5rem;
  --radius-lg: 0.75rem;
  --radius-xl: 1rem;
  --radius-2xl: 1.25rem;

  /* Shadows */
  --shadow-sm: 0 1px 2px 0 rgb(0 0 0 / 0.05);
  --shadow-md: 0 4px 6px -1px rgb(0 0 0 / 0.07), 0 2px 4px -2px rgb(0 0 0 / 0.05);
  --shadow-lg: 0 10px 15px -3px rgb(0 0 0 / 0.08), 0 4px 6px -4px rgb(0 0 0 / 0.05);

  /* Motion */
  --duration-fast: 150ms;
  --duration-normal: 300ms;
  --duration-slow: 500ms;
  --duration-reveal: 700ms;
  --ease-out: cubic-bezier(0.16, 1, 0.3, 1);
  --stagger-step: 80ms;
}
```

## Component inventory (shared shell — approved scope)

| Component | Status | Notes |
|-----------|--------|--------|
| StickyHeader | Delivered | Brand mark + wordmark + desktop nav + dropdowns + auth + menu toggle |
| BrandMark | Delivered | Gradient clock icon mark for dateandtime.live (header + footer) |
| AuthButtons | Delivered | Log in (soft blue gradient) + Sign up (blue→indigo→violet gradient) |
| NavDropdown | Delivered | World Time + Timezones (desktop hover/click panels) |
| MobileMenu | Delivered | Full-screen under header, grouped sections, auth row, Escape closes |
| Breadcrumb | Delivered | Home / current page |
| Footer | Delivered | Brand + World Time + Timezones + More (no Meeting Planner / standalone Converter) |
| NavLink | Delivered | `data-page` + `data-source` (Header \| Footer \| Breadcrumb) |
| PlaceholderPage | Delivered | “Clicked from [source] → [Page Name]” |

### Nav structure
- **World Time** menu: World Time · Personal World Time · For Your Site  
- **Timezones** menu: Timezone Converter · Timezone Difference · Daylight Saving Time  
- Removed from shell: Meeting Planner, standalone Converter (converter lives under Timezones)

## Future body components (not built yet)

SearchCity, LiveClock, CityCard, TimeZoneBadge, ToolCard, SnapshotCard, SectionHeader, Button, Badge, FAQ, FeedbackWidget, ProgressiveReveal, StaggerGrid.

## Next.js mapping (after visual LGTM)

```
components/shell/StickyHeader.tsx
components/shell/MobileMenu.tsx
components/shell/Breadcrumb.tsx
components/shell/Footer.tsx
components/shell/NavLink.tsx
app/layout.tsx   // composes shell
// API placeholders deferred until body sections need data
```
