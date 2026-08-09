# Motion Patterns (Vanilla JS + Tailwind)

Use these exact lightweight patterns in every prototype.

## Progressive Section Reveal

```html
<section class="section-reveal opacity-0 translate-y-6 transition-all duration-700 ease-out" data-reveal>
  ...
</section>
```

```js
const observer = new IntersectionObserver((entries) => {
  entries.forEach(entry => {
    if (entry.isIntersecting) {
      entry.target.classList.remove('opacity-0', 'translate-y-6');
      entry.target.classList.add('opacity-100', 'translate-y-0');
      observer.unobserve(entry.target);
    }
  });
}, { threshold: 0.12, rootMargin: '0px 0px -40px 0px' });

document.querySelectorAll('[data-reveal]').forEach(el => observer.observe(el));
```

## Top-to-Bottom Staggered Cards

```html
<div class="grid ...">
  <div class="card-stagger opacity-0 translate-y-4" data-stagger style="transition-delay: 0ms">...</div>
  <div class="card-stagger opacity-0 translate-y-4" data-stagger style="transition-delay: 80ms">...</div>
  <!-- increment by 60–100ms -->
</div>
```

```js
const staggerObserver = new IntersectionObserver((entries) => {
  entries.forEach(entry => {
    if (entry.isIntersecting) {
      entry.target.classList.remove('opacity-0', 'translate-y-4');
      entry.target.classList.add('opacity-100', 'translate-y-0');
      staggerObserver.unobserve(entry.target);
    }
  });
}, { threshold: 0.1 });

document.querySelectorAll('[data-stagger]').forEach(el => staggerObserver.observe(el));
```

## Card Hover

```html
<article class="group relative rounded-2xl border border-zinc-200 bg-white p-5 transition-all duration-300 hover:-translate-y-1 hover:shadow-lg hover:border-zinc-300">
```

## Reduced Motion

Always include:

```css
@media (prefers-reduced-motion: reduce) {
  .section-reveal, .card-stagger {
    opacity: 1 !important;
    transform: none !important;
    transition: none !important;
  }
}
```
