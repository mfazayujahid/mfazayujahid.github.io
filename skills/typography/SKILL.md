---
name: typography
description: >-
  Production-proven rules and standards for digital and editorial typography:
  modular scales, vertical rhythm, line length (measure), fluid sizing with clamp(),
  web font loading performance, font pairings, and broadsheet newspaper styling.
  Use this skill whenever styling text, configuring typography scales, selecting fonts,
  or refining mobile reading ergonomics.
---

# Typography: Production-Proven Standards & Guidelines

Typography is the foundation of user interface design and readability. This skill provides mathematical formulas, font loading optimization strategies, and editorial typesetting standards.

---

## 1. Typographic Hierarchy & Modular Scales

### 1.1 Modular Scale Ratios
A modular scale provides harmonic, proportional sizing from microcopy to grand mastheads:
* **Major Second (1.125):** Subtle scaling, ideal for dense technical dashboards and data tables.
* **Minor Third (1.200):** Balanced, clean scaling for mobile viewports.
* **Major Third (1.250):** Classic editorial scale, great for readable broadsheets.
* **Perfect Fourth (1.333):** Expressive, high-contrast scale for punchy editorial headlines.

### 1.2 Fluid Typography with `clamp()`
Hard-coded font sizes produce jarring jumps across device widths. Use fluid typography:
$$\text{font-size} = \text{clamp}(V_{\min}, \text{calc}(V_{\min} + S \cdot (100\text{vw} - W_{\min})), V_{\max})$$

Recommended responsive fluid presets:
```css
/* Masthead Headline */
--font-masthead: clamp(2.5rem, 1.8rem + 3.5vw, 5.5rem);

/* Lead Article Title (H1/H2) */
--font-headline: clamp(1.75rem, 1.3rem + 2vw, 3.25rem);

/* Section Subhead (H3/H4) */
--font-subhead: clamp(1.25rem, 1.1rem + 0.8vw, 1.75rem);

/* Body Text (Ensures >= 16px on mobile to avoid iOS Safari auto-zoom) */
--font-body: clamp(1rem, 0.95rem + 0.25vw, 1.125rem);

/* Microcopy / Captions / Typewriter */
--font-caption: clamp(0.75rem, 0.72rem + 0.15vw, 0.875rem);
```

---

## 2. Line Length (Measure) & Vertical Rhythm

### 2.1 Optimal Line Length (The Measure)
* **Body Copy:** Maintain **45 to 75 characters per line** (including spaces). Lines shorter than 40 characters break reading cadence; lines longer than 80 characters cause eye fatigue during line sweeps.
* **Max-Width Safeguards:** In CSS, apply `max-width: 65ch` (or column wrapping) on editorial paragraphs.

### 2.2 Line Height (Leading) Formula
* **Body Copy:** `1.5` to `1.65` for optimal readability in serif/sans body text.
* **Headlines / Display Text:** Tighter leading of `1.05` to `1.2` to prevent awkward vertical gaps between multi-line titles.
* **Rule:** As font size increases, decrease relative line-height proportionally.

---

## 3. Font Pairings & Editorial Styling

### 3.1 Classic Newspaper / Broadsheet Trinity
1. **Masthead / High Display:** Ornate serif or blackletter/classical roman (e.g., *Cinzel Decorative*, *Playfair Display*).
2. **Body & Story Dispatches:** High-legibility editorial serif with generous x-height and distinct italics (e.g., *Newsreader*, *Georgia*, *Merriweather*).
3. **Utility / Meta / Tech Dossiers:** Authentic typewriter monospace or clean technical grotesk (e.g., *Courier Prime*, *Special Elite*, *Inter*).

### 3.2 Authentic Editorial Flourishes
* **Drop Caps:**
  ```css
  .drop-cap::first-letter {
    font-family: 'Playfair Display', Georgia, serif;
    float: left;
    font-size: 3.5rem;
    line-height: 0.8;
    padding-top: 4px;
    padding-right: 8px;
    font-weight: 900;
  }
  @media (max-width: 768px) {
    .drop-cap::first-letter {
      font-size: 2.8rem;
      line-height: 0.85;
      padding-right: 6px;
    }
  }
  ```
* **Tabular Numbers:** Always use `font-variant-numeric: tabular-nums;` for data tables, metrics, stats, and timers so characters align vertically.
* **Small Caps & Tracking:** When using uppercase for subtitles or badges, increase letter-spacing (`tracking-wider` or `letter-spacing: 0.08em` to `0.15em`) and reduce font weight slightly to prevent visual heaviness.

---

## 4. Web Font Loading Performance

* **Eliminate FOIT (Flash of Invisible Text):** Always append `&display=swap` to Google Fonts and define `font-display: swap` in `@font-face`.
* **Resource Hints:**
  ```html
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  ```
* **Font Subsetting:** Request only needed weights and subsets (e.g. `latin`) to reduce WOFF2 payloads.

---

## 5. Typography Pre-Update Checklist

1. [ ] Body text never drops below 16px on mobile viewports.
2. [ ] `line-height` is proportional: headlines ~1.1–1.2, body copy ~1.5–1.65.
3. [ ] Paragraphs constrained to `max-width: 65ch` or within multi-column grid containers.
4. [ ] All web font links include `display=swap` and proper `preconnect` origins.
5. [ ] Punctuation, dashes, and quotes use correct typographical glyphs (`“ ”`, `‘ ’`, `—`, `–`).

