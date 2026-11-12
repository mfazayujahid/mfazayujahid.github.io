---
name: web-design
description: >-
  Production-proven rules and standards for modern responsive web design, layout composition,
  visual hierarchy, mobile-first design, UI interaction states, and accessibility (WCAG 2.1 AA).
  Use this skill whenever designing, reviewing, or updating web pages, UI layouts, components,
  or theme systems.
---

# Web Design: Production-Proven Standards & Guidelines

This skill provides an authoritative, battle-tested reference for building high-quality, responsive, accessible, and visually stunning web interfaces.

---

## 1. Layout & Grid Architecture

### 1.1 Responsive Fluid Grid Systems
* **Fluid Columns & Margins:** Use flexible grid containers (`display: grid` or `display: flex`) with fluid sizing (`minmax()`, `auto-fit`, `auto-fill`, `fr` units).
* **Viewport Safety & Overflow:**
  * Never allow horizontal scrolling (`overflow-x: hidden` on viewport roots when decorative elements overflow).
  * Always set `box-sizing: border-box` globally across `*, *::before, *::after`.
  * Set `max-width: 100%` on all images, videos, canvas, and media embeds.
* **Standard Breakpoints:**
  * `xs`: `< 480px` (Compact mobile)
  * `sm`: `480px - 767px` (Large mobile / phablet)
  * `md`: `768px - 1023px` (Tablet)
  * `lg`: `1024px - 1279px` (Desktop / Laptop)
  * `xl`: `1280px+` (Wide desktop / broadsheet)

### 1.2 Visual Hierarchy & Composition
* **The 60-30-10 Color Rule:**
  * **60% Dominant Base:** Background and neutral paper/canvas surfaces (e.g., `#f5f0ea` / dark `#181716`).
  * **30% Secondary Structure:** Structural borders, body copy ink, and secondary cards (e.g., `#2c2523`, `#4a423e`).
  * **10% Accent / Focal:** High-contrast accent reserved strictly for key CTAs, stamps, badges, and alerts (e.g., `#8a1c14`, `#ff6b5e`).
* **Z-Pattern & F-Pattern Scanning:**
  * Place high-priority anchors (masthead, primary CTA, breaking ticker) along natural reading axes.
  * Anchor each section with a distinct headline and clear sub-lead before diving into columnar details.

---

## 2. Interactive Affordances & State Management

### 2.1 Touch & Click Targets
* **Minimum Target Size:** All interactive elements (`button`, `a`, input controls) must maintain a minimum bounding box of **44×44px** (or minimum `40px` with at least 8px surrounding touch padding) to comply with WCAG 2.5.5.
* **Clear Cursor & Hover Feedback:**
  * Always assign `cursor: pointer` to clickable items.
  * Provide instantaneous visible feedback on `:hover`, `:active`, and `:focus-visible`.

### 2.2 Accessible Focus Indicators
* Never strip `outline: none` without providing an explicit `:focus-visible` ring (e.g., `focus-visible:ring-2 focus-visible:ring-paper-red`).
* Ensure keyboard navigability (`Tab`, `Shift+Tab`, `Enter`, `Space`, `Escape` for modals).

### 2.3 Motion & Transitions
* Limit transition durations to **150ms – 300ms** for micro-interactions (hover, active, toggle).
* Use cubic-bezier easing (`cubic-bezier(0.16, 1, 0.3, 1)` or `ease-out`) rather than linear for UI transforms.
* **Always honor reduced motion:**
  ```css
  @media (prefers-reduced-motion: reduce) {
    *, *::before, *::after {
      animation-duration: 0.01ms !important;
      animation-iteration-count: 1 !important;
      transition-duration: 0.01ms !important;
      scroll-behavior: auto !important;
    }
  }
  ```

---

## 3. Accessibility & Contrast (WCAG 2.1 AA)

* **Minimum Contrast Ratios:**
  * Normal text (`< 18pt` or `< 14pt bold`): Minimum **4.5:1** contrast ratio against its background.
  * Large text (`>= 18pt` or `>= 14pt bold`): Minimum **3:1** contrast ratio.
  * UI components and graphical objects: Minimum **3:1** contrast ratio.
* **Color Independence:** Never convey information solely through color; always pair colors with icons, labels, or typographical distinctions (e.g., bold weights, underlines).

---

## 4. Dark Mode & Dual-Theming Architecture

* **Theme Variables / Class Toggling:**
  * Use CSS custom properties or declarative utility classes (`dark:`, `.evening-edition`) targeting the `<body>` or `<html>` element.
* **Contrast Preservation in Dark Mode:**
  * Do not use pure `#000000` with pure `#ffffff` text, as this causes harsh visual halation/glare.
  * Use warm charcoals (e.g., `#141312`, `#1f1d1b`) paired with warm cream or aged newsprint parchment (e.g., `#ede5da`, `#f7f3ed`).
* **Preference Persistence:**
  * Check `localStorage` first; fall back gracefully to `window.matchMedia('(prefers-color-scheme: dark)')`.

---

## 5. Web Design Pre-Update Checklist

1. [ ] No unexpected horizontal scrollbars on mobile viewports (< 375px, 414px, 768px).
2. [ ] All buttons and links have distinct hover, focus-visible, and active states.
3. [ ] Contrast ratio meets or exceeds 4.5:1 for body copy and 3:1 for large text.
4. [ ] Modals trap focus, close on `Escape` and backdrop click, and restore scroll position.
5. [ ] Print styles hide navigation bars, interactive audio/toggles, and paginate cleanly.
