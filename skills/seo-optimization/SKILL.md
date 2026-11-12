---
name: seo-optimization
description: >-
  Production-proven checklist and specifications for technical SEO, semantic HTML5,
  Schema.org JSON-LD structured data, Open Graph / Twitter metadata, Core Web Vitals
  (LCP, CLS, INP), and multilingual search engine visibility. Use this skill whenever
  auditing, configuring, or updating SEO metadata, structured data, or page performance.
---

# SEO Optimization: Production-Proven Standards & Guidelines

Technical SEO ensures that search engines, social crawlers, and AI-powered answer engines can accurately parse, index, and surface a web property with maximum authority.

---

## 1. Document Head & Metadata Architecture

### 1.1 Essential Primary Meta Tags
Every production HTML document must declare:
```html
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Accurate, Compelling Title (50-60 characters)</title>
<meta name="description" content="Engaging summary with primary keywords (140-160 characters).">
<meta name="author" content="Full Name">
<meta name="robots" content="index, follow, max-image-preview:large, max-snippet:-1, max-video-preview:-1">
<link rel="canonical" href="https://yourdomain.com/">
```

### 1.2 Open Graph (OG) Protocol for Social Crawlers
Ensures rich embeds on LinkedIn, WhatsApp, Telegram, Twitter/X, Discord, Slack:
```html
<!-- Open Graph / Facebook / LinkedIn / WhatsApp -->
<meta property="og:type" content="website">
<meta property="og:site_name" content="Site Title">
<meta property="og:url" content="https://yourdomain.com/">
<meta property="og:title" content="Compelling Embed Title">
<meta property="og:description" content="Crisp summary highlighting value proposition and achievements.">
<meta property="og:image" content="https://yourdomain.com/assets/img/og-preview.jpg">
<meta property="og:image:width" content="1200">
<meta property="og:image:height" content="630">
<meta property="og:image:alt" content="Descriptive text of the preview image">
<meta property="og:locale" content="en_US">
<meta property="og:locale:alternate" content="id_ID">

<!-- Twitter Cards -->
<meta name="twitter:card" content="summary_large_image">
<meta name="twitter:url" content="https://yourdomain.com/">
<meta name="twitter:title" content="Compelling Embed Title">
<meta name="twitter:description" content="Crisp summary highlighting value proposition and achievements.">
<meta name="twitter:image" content="https://yourdomain.com/assets/img/og-preview.jpg">
```

---

## 2. Schema.org JSON-LD Structured Data

Google and search bots parse JSON-LD to generate rich knowledge panels and search snippets.

### 2.1 Person & ProfilePage Schema for Engineering Portfolios
Place inside `<script type="application/ld+json">` in `<head>`:
```json
{
  "@context": "https://schema.org",
  "@graph": [
    {
      "@type": "ProfilePage",
      "@id": "https://mfazayujahid.dev/#profilepage",
      "url": "https://mfazayujahid.dev/",
      "name": "Muhammad Faza Yujahid - Full-Stack & Backend Engineer",
      "isPartOf": {
        "@type": "WebSite",
        "@id": "https://mfazayujahid.dev/#website",
        "url": "https://mfazayujahid.dev/",
        "name": "The Faza Chronicle"
      },
      "about": {
        "@id": "https://mfazayujahid.dev/#author"
      },
      "mainEntity": {
        "@id": "https://mfazayujahid.dev/#author"
      }
    },
    {
      "@type": "Person",
      "@id": "https://mfazayujahid.dev/#author",
      "name": "Muhammad Faza Yujahid",
      "jobTitle": "Full-Stack Web Developer",
      "description": "Full-Stack and Backend Architect specializing in Node.js, Go, React, and PostgreSQL enterprise systems.",
      "address": {
        "@type": "PostalAddress",
        "addressLocality": "Bandung",
        "addressRegion": "West Java",
        "addressCountry": "ID"
      },
      "sameAs": [
        "https://www.linkedin.com/in/mfazayujahid/",
        "https://github.com/mfazayujahid"
      ],
      "knowsAbout": [
        "Full-Stack Development",
        "Backend Architecture",
        "Node.js",
        "Go (Golang)",
        "PostgreSQL",
        "ReactJS",
        "VueJS",
        "Valhalla OpenStreetMap",
        "Google BigQuery",
        "Microservices"
      ]
    }
  ]
}
```

---

## 3. Core Web Vitals Optimization (SEO Ranking Factors)

Search engines directly penalize poor page speed and layout instability:

### 3.1 Largest Contentful Paint (LCP)
* **Goal:** $< 2.5\text{s}$.
* **Image Optimization:** Preload hero/profile image or give it `fetchpriority="high"`.
* **Zero External Blocker:** Serve critical fonts with `preconnect` and `display=swap`.

### 3.2 Cumulative Layout Shift (CLS)
* **Goal:** $< 0.1$.
* **Explicit Dimensions:** Declare explicit `width` and `height` (or aspect-ratio CSS) on all `<img>`, `<video>`, and icons.
* **Font Fallbacks:** Match fallback font metrics (`size-adjust`, `ascent-override`) to avoid layout jumps when web fonts swap.

### 3.3 Interaction to Next Paint (INP)
* **Goal:** $< 200\text{ms}$.
* Keep JavaScript task execution light; yield to the main thread during heavy operations.

---

## 4. Semantic Hierarchy & Link Architecture

* **Strict Single `<h1>` Rule:** Exactly one prominent `<h1>` per page (the Masthead title or primary page subject).
* **Cascading Headings:** Never skip levels (`<h1>` $\rightarrow$ `<h2>` $\rightarrow$ `<h3>`).
* **Descriptive Anchor Text:** Never use "click here" or "read more" in isolation. Use descriptive text (e.g., "Inspect ERP System Architecture Dispatch").
* **Outbound Link Security:** All external links (`target="_blank"`) must specify `rel="noopener noreferrer"` to protect against reverse tabnabbing and preserve performance.

---

## 5. SEO Pre-Update Checklist

1. [ ] Title tag is between 50 and 60 characters and unique.
2. [ ] Meta description is between 140 and 160 characters.
3. [ ] Canonical link tag is declared with absolute URL.
4. [ ] Open Graph and Twitter Card tags are populated with preview images and descriptions.
5. [ ] Valid JSON-LD structured data is embedded and syntax-checked.
6. [ ] All images have descriptive `alt` attributes, explicit `width` and `height`, and appropriate loading strategies.
7. [ ] Single `<h1>` tag with proper descending heading structure (`<h2>`, `<h3>`).
8. [ ] External links include `rel="noopener noreferrer"`.

