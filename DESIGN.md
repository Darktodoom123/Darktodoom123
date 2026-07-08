# Design System

## Theme: Celestial Space & Gradients

A premium, immersive, dark celestial theme featuring deep cosmic purples, glowing nebula gradients, and sharp glassmorphic elements. The interface uses glowing interactive highlights and clean sans-serif typography.

### Color Palette (OKLCH)

```css
:root {
  /* Backgrounds & Surfaces */
  --bg-deep: oklch(14% 0.04 275);      /* Space Black-Indigo: body background */
  --bg-surface: oklch(18% 0.05 280);   /* Nebula Deep: card and surface background */
  --bg-glow: oklch(24% 0.08 285 / 0.4); /* Glow surface for glass effects */

  /* Brand Accents */
  --color-primary: oklch(62% 0.18 295);  /* Cosmic Purple: main brand color */
  --color-secondary: oklch(74% 0.16 325);/* Stardust Magenta: vibrant secondary */
  --color-accent: oklch(80% 0.14 195);   /* Astral Teal: interactive highlight */

  /* Borders & Outlines */
  --border-subtle: oklch(28% 0.06 280 / 0.5); /* Deep border */
  --border-glow: oklch(62% 0.18 295 / 0.3);   /* Glow state border */

  /* Ink & Typography */
  --ink-primary: oklch(98% 0.01 270);    /* Soft Cosmic White: main text */
  --ink-secondary: oklch(85% 0.02 270);  /* Nebula Silver: secondary/body text */
  --ink-muted: oklch(68% 0.03 270);      /* Stardust Gray: placeholder/muted text */
}
```

---

### Typography

* **Headings**: `Outfit`, sans-serif (Display, Hero, Section Headings). Heavy weights (700, 800) with letter-spacing clamped to avoid touching.
* **Body / Interface**: `Inter`, sans-serif (Body text, UI elements, button labels). Weights (400, 500, 600) for high readability.

```css
h1, h2, h3 {
  font-family: 'Outfit', sans-serif;
  color: var(--ink-primary);
  text-wrap: balance;
}

body {
  font-family: 'Inter', sans-serif;
  color: var(--ink-secondary);
  line-height: 1.6;
  max-width: 75ch; /* Comfortable reading length */
}
```

---

### Spacing & Layout

* **Rhythm**: Varied spacing between sections to avoid uniform grids.
* **Responsive Layouts**: Flexible flexbox and CSS grids without hard breakpoints using clamp functions.
* **Responsive Cards**: Spacing clamped between `1.5rem` (mobile) and `2.5rem` (desktop).

```css
.grid-showcase {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
  gap: 2rem;
}
```

---

### Component Specifications

#### 1. Interactive Cards
* **Border Radius**: `12px` (maximum `16px`).
* **Border**: `1px solid var(--border-subtle)`.
* **State Change**: On hover, background shifts to a subtle translucent gradient, border becomes `var(--border-glow)`, and a soft box-shadow (`box-shadow: 0 8px 30px oklch(62% 0.18 295 / 0.1)`) is applied. (Strictly avoiding double-border/double-wide-shadow tells).

#### 2. Skill Nodes
* Dynamic circular badges or interconnected nodes showing technologies.
* Interactive scale transitions (`transform: scale(1.05)`) with ease-out-expo timing.

#### 3. Buttons & Tabs
* Active states utilize subtle glow underlays.
* Tags use `full-pill` (`border-radius: 9999px`) styling.

---

### Motion & Transitions

* **Easing Function**: Custom exponential curves for luxury feel.
  `transition: all 400ms cubic-bezier(0.16, 1, 0.3, 1);` (ease-out-expo)
* **Reduced Motion**: All reveal transitions fallback to simple opacity crossfades.

```css
@media (prefers-reduced-motion: reduce) {
  * {
    animation-delay: 0s !important;
    animation-duration: 0s !important;
    animation-iteration-count: 1 !important;
    transition-duration: 0s !important;
    scroll-behavior: auto !important;
    transform: none !important;
  }
}
```
