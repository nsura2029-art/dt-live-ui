# 21st.dev-inspired Consistency Rules

21st.dev is a large registry of React + Tailwind components (many shadcn-compatible). Its core value is high-quality, copyable, owned components that compose cleanly inside a design system.

When recreating patterns for this skill:

1. Define every UI primitive once in the direction’s component inventory.
2. Reuse the exact same HTML structure, Tailwind classes, and interaction behavior on every page.
3. Prefer a small set of well-crafted variants (size, intent, density) over many unique one-offs.
4. Motion, hover, and focus states must be identical wherever the component appears.
5. When a new need arises later, extend the shared inventory first, then use the new variant everywhere it is needed.

Never treat a component as “page-specific.” The same card, button, clock face, badge, or data row must look and behave the same on Home, World Clock, Meeting Planner, and every other page of that design direction.