# YSSF Design System & UI/UX Guidelines

> **Youth Sakti Social Foundation (YSSF)**
> A modern NGO Ecosystem Platform blending a youthful, handmade aesthetic with modern web capabilities.

This document serves as the single source of truth for the visual identity, UI components, and interaction patterns of the YSSF platform. It is designed to work seamlessly with our tech stack: **Next.js, Tailwind CSS, Framer Motion, and Three.js.**

---

## 📑 Table of Contents

1. [Brand Vision & Core Philosophy](#1-brand-vision--core-philosophy)
2. [Color Palette & Tailwind Tokens](#2-color-palette--tailwind-tokens)
3. [Typography System](#3-typography-system)
4. [UI Components & Forms](#4-ui-components--forms)
5. [Motion & Animation (Framer Motion)](#5-motion--animation-framer-motion)
6. [Layout, Spacing & Grid](#6-layout-spacing--grid)
7. [Media, 3D & Illustration](#7-media-3d--illustration)
8. [Accessibility (A11y)](#8-accessibility-a11y)
9. [Design Checklist](#9-design-checklist)

---

## 1. Brand Vision & Core Philosophy

### The Core Vibe
YSSF represents **Nature, Humanity, Community, Awareness, and Youth Energy.** 
The platform should feel:
- **Warm & Emotional:** Engaging storytelling through visuals.
- **Hand-crafted:** Slight "school-project" or organic aesthetic.
- **Clean but Alive:** Not a stiff corporate site, but highly usable.
- **Modern Ecosystem:** Seamless dashboard and donation flows.

> **Design Motto:** *"Small actions together can create a lasting impact."*

**Avoid:** Corporate stiffness, heavy glassmorphism, overly dark/cyber themes, aggressive neon effects.

---

## 2. Color Palette & Tailwind Tokens

Our color system uses nature-inspired greens combined with energetic youth-focused accents. 

### Core Theme (`tailwind.config.ts` mapping)

| Role | Color Name | Hex Code | Tailwind Token | Usage |
| :--- | :--- | :--- | :--- | :--- |
| **Primary** | Deep Forest Green | `#0B5D3B` | `bg-primary-900` | Main branding, navbars, hero headings. |
| **Secondary**| Light Leaf Green | `#8FD694` | `bg-primary-400` | Cards, highlight sections, soft borders. |
| **Accent** | Deep Yellow | `#F4B400` | `bg-accent-500` | Primary CTA buttons, accent glows, urgent highlights. |
| **Surface** | Mint Green | `#DFF7E2` | `bg-surface-100` | Background tints, alternating sections. |
| **Base** | Pure White | `#FFFFFF` | `bg-white` | Main app background, card backgrounds. |

### Semantic & Support Colors

| Role | Color Name | Hex Code | Tailwind Token | Usage |
| :--- | :--- | :--- | :--- | :--- |
| **Danger/Alert** | Warm Red | `#D64545` | `bg-alert-500` | Emergency campaigns, form errors, destructive actions. |
| **Warning/Hover**| Soft Orange | `#F57C00` | `bg-warning-500`| Awareness tags, hover accents on yellow buttons. |

---

## 3. Typography System

We use a 4-font combination to achieve the "Modern Startup meets Handmade Poster" aesthetic.

### Font Configurations

1. **Gochi Hand** (Handwritten & Emotional)
   - **Tailwind:** `font-handwritten`
   - **Usage:** Hero heading highlights, emotional quotes, custom brush-stroke sections.
2. **Patrick Hand** (Friendly & Structured)
   - **Tailwind:** `font-display`
   - **Usage:** Subheadings, small banners, campaign cards, awareness section titles.
3. **Poppins** (Clean & Modern)
   - **Tailwind:** `font-heading`
   - **Usage:** Main UI elements, buttons, navbar links, dashboard headers.
4. **Nunito** (Soft & Readable)
   - **Tailwind:** `font-sans` (Default body)
   - **Usage:** Section descriptions, body paragraphs, testimonials, footers.

*Ensure all fonts are optimized using `next/font` for zero layout shift.*

---

## 4. UI Components & Forms

### Buttons (`React Aria` compliant)

**Primary CTA**
- **Style:** Deep Yellow background (`bg-accent-500`), Deep Green text (`text-primary-900`).
- **Radius:** `rounded-2xl` (16px).
- **Hover State:** Slight scale up (`hover:scale-105`), soft orange shadow (`hover:shadow-warning/50`).

**Secondary CTA (Outline)**
- **Style:** Transparent background, Deep Green border (`border-2 border-primary-900`), Deep Green text.
- **Hover State:** Mint background (`hover:bg-surface-100`).

### Cards
Cards are the primary container for campaigns, events, and blogs.
- **Radius:** `rounded-3xl` (20px) for a soft, friendly feel.
- **Shadow:** Soft, organic shadow (`shadow-soft` -> custom tailwind token).
- **Interaction:** Slight hover lift (`hover:-translate-y-1 hover:shadow-lg`).
- **Backgrounds:** White or Light Mint Gradient.

---

## 5. Motion & Animation (Framer Motion)

Animations should feel **Soft, Friendly, Lightweight, and Natural.**

### Standard Variants

```javascript
// 1. Soft Fade Up (For sections & cards)
export const fadeUp = {
  hidden: { opacity: 0, y: 30 },
  visible: { opacity: 1, y: 0, transition: { duration: 0.6, ease: "easeOut" } }
};

// 2. Hover Bounce (For buttons)
export const hoverBounce = {
  hover: { scale: 1.05, transition: { type: "spring", stiffness: 300 } },
  tap: { scale: 0.95 }
};

// 3. Staggered Children (For lists of campaigns)
export const staggerContainer = {
  hidden: { opacity: 0 },
  visible: {
    opacity: 1,
    transition: { staggerChildren: 0.15 }
  }
};
```

*Avoid:* Aggressive spring physics, overly techy glitch effects, or long unskippable loaders.

---

## 6. Layout, Spacing & Grid

Adopt a **Mobile-First Priority**. The platform must be fast, lightweight, and touch-friendly.

### Standard Spacing Tokens
| Type | Value | Tailwind Class |
| :--- | :--- | :--- |
| **Section Padding** | `100px` | `py-24` |
| **Card Padding** | `24px` | `p-6` |
| **Button Padding** | `14px 28px` | `px-7 py-3.5` |
| **Container Max-Width** | `1280px` | `max-w-7xl mx-auto` |

### Responsive Behavior
- **Mobile (`< 768px`):** Stacked cards, full-width buttons, readable font sizes (minimum 16px body).
- **Tablet (`768px - 1024px`):** 2-column grids for campaigns.
- **Desktop (`> 1024px`):** 3-column grids, visible sidebars for dashboards, parallax effects enabled.

---

## 7. Media, 3D & Illustration

### Photography Style
Images must feel **Real, Emotional, and Hopeful.**
- **Subjects:** Volunteers planting trees, real community smiles, blood donation camps, nature restoration.
- **Lighting:** Natural lighting, warm tones. No overly corporate stock photos.
- **Treatment:** Slight rounded corners (`rounded-2xl`).

### Three.js & Interactive Visuals
Use `Three.js` sparingly for storytelling, not just decoration:
- Floating 3D leaves on the Hero Section.
- Interactive globe highlighting areas of impact.
- Soft particle systems (representing seeds/growth) during donation success screens.

### Textures & Backgrounds
- Use paper textures, watercolor overlays, and organic SVG blobs behind content sections to break up straight grid lines.

---

## 8. Accessibility (A11y)

We build for everyone. YSSF must comply with WCAG standards.
- **Contrast:** Ensure `Deep Forest Green` on `Mint Green` or `White` passes contrast checks. 
- **Focus Rings:** Use `React Aria` to provide clear, custom focus rings for keyboard navigation (`focus-visible:ring-2 focus-visible:ring-accent-500`).
- **Screen Readers:** All icons must have `aria-label` or `sr-only` fallback text. Images must have descriptive `alt` tags.

---

## 9. Design Checklist

Before merging PRs or finalizing any page component, review this checklist:

- [ ] **Vibe Check:** Does it feel human, hopeful, and community-driven?
- [ ] **Color Balance:** Is the green palette dominant without being overwhelming?
- [ ] **Typography:** Are the 4 fonts used semantically? (Gochi for emotion, Poppins for UI).
- [ ] **Motion:** Are the Framer Motion animations soft and natural?
- [ ] **Responsiveness:** Is the layout perfectly usable on mobile devices?
- [ ] **Accessibility:** Can the section be navigated entirely by keyboard?
- [ ] **Performance:** Are images optimized (via Cloudinary/Next Image) and 3D elements lazily loaded?

---
*End of Design System Document*