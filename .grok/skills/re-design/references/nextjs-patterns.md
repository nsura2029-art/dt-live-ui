# Next.js Patterns for re-design

## Default Approach

- App Router (`app/` directory)
- Server Components by default
- `"use client"` only for interactive pieces (clocks that tick, mobile menu, hover-heavy cards if needed, Intersection Observer reveals)
- Tailwind CSS for styling
- Shared components live in a consistent location (e.g. `components/ui/` or `components/time/`)

## API Placeholders (always leave these)

### Data fetching (Server Component)
```tsx
// TODO: replace with real data source
// const cities = await fetch(`${process.env.API_BASE}/world-clock`, {
//   next: { revalidate: 30 }
// }).then(r => r.json())

const cities = PLACEHOLDER_CITIES
```

### Server Action
```tsx
// async function saveFavorite(formData: FormData) {
//   'use server'
//   // await db.favorites.create(...)
// }
```

### Client-side fetch (when needed)
```tsx
// useEffect(() => {
//   fetch('/api/current-time')
//     .then(r => r.json())
//     .then(setTime)
// }, [])
```

## Reusability Rule (Components First)

Every component must be importable and usable on any page of the same design direction without modification. Props interfaces stay stable. Variants are controlled via props or className, never by rewriting the component per page.

**Mandatory order of work:**
1. Define the full shared component library for the direction (SearchCity, LiveClock, CityCard, TimeZoneBadge, StickyNav, MobileMenu, Button, etc.).
2. Get LGTM on the components.
3. Only then compose page sections by importing and using those components.
4. Never write a search input, card, or clock inline inside a page section. Always import the shared one.

## Motion

Prefer a single shared `Reveal` or `Stagger` client component that uses Intersection Observer. Import and wrap sections/cards with it rather than duplicating observer logic.