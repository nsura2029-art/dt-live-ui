---
name: re-design
description: Create 5 premium mobile-first light-mode designs for date-and-time utility apps (dateandtime.live style). Use when user says design premium mobile-first time apps, redesign time app, or requests section-by-section premium prototypes with design systems. Always builds shared reusable components first (SearchCity, LiveClock, CityCard, etc.) then composes pages from them. Produces full tokens, typography, components inspired by 21st.dev and beui.dev. Default stack is Next.js App Router (SSR + client components) with API placeholders. Supports pure HTML + Tailwind CDN when requested. Enforces components-first, section-by-section LGTM, and isolated edits.
---

# Re-Design

Premium mobile-first redesign skill for date-and-time utility products. Always produce light-mode only designs that feel information-rich yet elegant.

## Core Rules

- Default output: exactly 3 distinct visual directions for the same feature set (user can request more).
- Default stack: Next.js App Router (React Server Components + client components where needed) + Tailwind CSS. Leave clear, well-commented placeholders for API integration (fetch, server actions, or route handlers). Pure HTML + Tailwind CDN + light vanilla JS is available only when the user explicitly requests it.
- Components: recreate patterns inspired by 21st.dev and beui.dev as clean, reusable HTML/CSS/JS pieces that live in the design system. Never copy external code verbatim.
- Component consistency is non-negotiable. Once a component (card, button, clock display, nav item, data row, badge, etc.) is defined for a direction, the identical markup structure, class names, variants, and behavior must be reused on every page of that direction. Do not invent one-off versions.
- Visual language: progressive section reveals, top-to-bottom staggered card loading, subtle card hover states, sticky navigation + mobile menu, fully responsive (mobile-first).
- References for density and hierarchy: timeanddate.com and Britannica biography pages.
- Design system is mandatory and must be frozen early. After the first LGTM on a page, tokens stay stable; only tiny additive updates are allowed later.

## Workflow (strict)

1. **Always start with the shared shell (Step 1 — mandatory first deliverable):**  
   Create Header + MobileMenu + Breadcrumb + Footer for the design direction(s).  
   - Desktop and mobile layouts must both work.  
   - Mobile menu must open/close correctly.  
   - Every link in Header and Footer must be clickable and load a simple placeholder page that says “Clicked from [Header/Footer] → [Page Name]”.  
   - Deliver a full self-contained HTML preview (or multiple if several design systems) so the user can open it in a new tab.  
   Wait for LGTM on the shell before any body sections.
2. After shell LGTM, identify remaining reusable components (SearchCity, LiveClock, CityCard, etc.) and present them next if needed.
3. Propose section order for the chosen page. Wait for approval.
4. Design and present **one section only**, composing it exclusively from the already-approved shared components. Always include a visual HTML preview. Stop and wait for explicit LGTM.
5. Only after LGTM move to the next section.
6. Repeat until the page is complete, then offer the next page or remaining directions.
7. When the user later says “redesign only the [section name]”:
   - Change solely that section.
   - Leave every other section on the page and all other pages completely untouched.
   - Keep design-system tokens frozen except for minimal necessary additions.
   - If a component itself needs change, update the shared component and note that it will affect all pages that use it.

Never redesign multiple body sections in one response unless the user explicitly asks.  
Never create a search box, card, button, or any other UI element more than once. Always define it as a shared component and reuse it.

## Required Design System (every direction)

Produce a compact, copy-pasteable token block that includes:

- Color tokens (semantic primary/accent, surfaces, borders, muted text, success/warning if needed)
- Typography scale + font pairings (choose a premium, legible system or Google font stack; use a distinctive but restrained display treatment for the large live clock)
- Spacing scale
- Border-radius scale
- Shadow scale
- Motion tokens (durations, easings, stagger delays)

Also list the reusable component inventory with variants (SearchCity, LiveClock, CityCard, TimeZoneBadge, StickyNav, MobileMenu, Button, Badge, etc.). Treat this inventory as the single source of truth. Every section on every page must import and compose from these components only — never recreate them inline.

## Prototype Requirements (Next.js default)

- Use Next.js App Router structure (app/ directory conventions).
- Prefer Server Components for static or data-fetched sections. Mark interactive pieces with `"use client"`.
- Leave clear placeholders for API integration, e.g.:
  ```tsx
  // TODO: replace with real API call
  // const data = await fetch('/api/world-clock', { next: { revalidate: 30 } }).then(r => r.json())
  const data = PLACEHOLDER_WORLD_CLOCK_DATA
  ```
  or
  ```tsx
  // Server Action placeholder
  // async function updateFavorites(formData: FormData) { 'use server' ... }
  ```
- Components must be fully reusable across pages (same import path and props interface).
- Include progressive-reveal and staggered-loading via a lightweight client component (Intersection Observer) or pure CSS where possible.
- Sticky header + accessible mobile menu required.
- All interactive states (hover, focus, active) present.
- Semantic HTML + basic accessibility (ARIA, reduced-motion media query).
- When pure HTML is requested instead: fall back to single self-contained HTML + Tailwind CDN + inline vanilla JS.

## 3 Directions Guidance (default)

When generating the default set of 3, deliberately vary the aesthetic axes while staying premium and light-mode:

- Editorial / Swiss clarity
- Soft utility density
- Refined monochrome + single accent

Each direction must still feel like the same product (same features, same information hierarchy) only with a different visual system. User can request more directions.

## Section Redesign Rule

On any later request to change a single section:

- Re-output only the updated HTML for that section (or the minimal surrounding context needed).
- Explicitly state that all other sections remain unchanged.
- Do not regenerate the full page or touch tokens unless a tiny additive token is required.
- If the requested change requires a new component variant, add it to the shared inventory first and note the addition. Never create a page-local or section-local component.

## Output Format

For every component set or section delivered:

1. Short rationale (1–2 sentences) for the visual choices.
2. The complete, ready-to-use Next.js component(s) or page section.
3. **Mandatory visual HTML preview** — a single, self-contained HTML file (Tailwind CDN + the exact markup/styles of the component or section) that the user can open or view immediately. This preview is required on every response so the user can see the result before giving LGTM.
4. Any new or updated design tokens (keep changes minimal after freeze).
5. Clear “Waiting for LGTM on this section” stop.

Never ask for LGTM without first providing the visual HTML preview.

When a full page or full set of 5 is complete, also provide the consolidated design-system token file for that direction.

## Anti-patterns

- Do not produce dark mode.
- Do not redesign untouched sections.
- Do not skip the LGTM gate.
- Do not invent heavy animation libraries or external dependencies beyond what is standard in a Next.js + Tailwind project.
- Do not hard-code real API endpoints or secrets. Always leave clear, commented placeholders.
- Do not make the designs sparse or “startup landing page” empty. Keep them information-rich and useful.
- Do not create one-off components or divergent variants for different pages. Consistency and reusability across all pages of a direction are mandatory.
- Do not redefine a component’s structure or classes after it has been LGTM’d in an earlier section.
- Do not recreate any UI element (search, card, clock, button, badge, nav item, etc.) more than once. Always create it once as a shared component and reuse it.
- Do not request LGTM without first delivering a self-contained HTML preview of the component or section.