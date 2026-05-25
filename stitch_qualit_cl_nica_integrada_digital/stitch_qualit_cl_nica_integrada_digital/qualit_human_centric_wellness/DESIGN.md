---
name: Qualité Human-Centric Wellness
colors:
  surface: '#f9f9fb'
  surface-dim: '#d9dadc'
  surface-bright: '#f9f9fb'
  surface-container-lowest: '#ffffff'
  surface-container-low: '#f3f3f5'
  surface-container: '#edeef0'
  surface-container-high: '#e8e8ea'
  surface-container-highest: '#e2e2e4'
  on-surface: '#1a1c1d'
  on-surface-variant: '#4a454e'
  inverse-surface: '#2f3132'
  inverse-on-surface: '#f0f0f2'
  outline: '#7b757f'
  outline-variant: '#ccc4cf'
  surface-tint: '#6c538b'
  primary: '#6a5188'
  on-primary: '#ffffff'
  primary-container: '#8369a3'
  on-primary-container: '#fffbff'
  inverse-primary: '#d8bafa'
  secondary: '#625981'
  on-secondary: '#ffffff'
  secondary-container: '#dacefd'
  on-secondary-container: '#5f567e'
  tertiary: '#735c00'
  on-tertiary: '#ffffff'
  tertiary-container: '#cca72f'
  on-tertiary-container: '#4e3d00'
  error: '#ba1a1a'
  on-error: '#ffffff'
  error-container: '#ffdad6'
  on-error-container: '#93000a'
  primary-fixed: '#eedbff'
  primary-fixed-dim: '#d8bafa'
  on-primary-fixed: '#260e43'
  on-primary-fixed-variant: '#543b71'
  secondary-fixed: '#e7deff'
  secondary-fixed-dim: '#ccc0ee'
  on-secondary-fixed: '#1e1539'
  on-secondary-fixed-variant: '#4a4168'
  tertiary-fixed: '#ffe088'
  tertiary-fixed-dim: '#e9c349'
  on-tertiary-fixed: '#241a00'
  on-tertiary-fixed-variant: '#574500'
  background: '#f9f9fb'
  on-background: '#1a1c1d'
  surface-variant: '#e2e2e4'
typography:
  display-lg:
    fontFamily: Quicksand
    fontSize: 48px
    fontWeight: '700'
    lineHeight: 56px
    letterSpacing: -0.02em
  display-lg-mobile:
    fontFamily: Quicksand
    fontSize: 32px
    fontWeight: '700'
    lineHeight: 40px
    letterSpacing: -0.02em
  headline-md:
    fontFamily: Quicksand
    fontSize: 32px
    fontWeight: '600'
    lineHeight: 40px
  headline-sm:
    fontFamily: Quicksand
    fontSize: 24px
    fontWeight: '600'
    lineHeight: 32px
  title-lg:
    fontFamily: Be Vietnam Pro
    fontSize: 20px
    fontWeight: '600'
    lineHeight: 28px
  body-lg:
    fontFamily: Be Vietnam Pro
    fontSize: 18px
    fontWeight: '400'
    lineHeight: 28px
  body-md:
    fontFamily: Be Vietnam Pro
    fontSize: 16px
    fontWeight: '400'
    lineHeight: 24px
  label-md:
    fontFamily: Be Vietnam Pro
    fontSize: 14px
    fontWeight: '500'
    lineHeight: 20px
    letterSpacing: 0.01em
  caption:
    fontFamily: Be Vietnam Pro
    fontSize: 12px
    fontWeight: '400'
    lineHeight: 16px
rounded:
  sm: 0.5rem
  DEFAULT: 1rem
  md: 1.5rem
  lg: 2rem
  xl: 3rem
  full: 9999px
spacing:
  base: 8px
  xs: 4px
  sm: 12px
  md: 24px
  lg: 48px
  xl: 80px
  container-max: 1200px
  gutter: 24px
---

## Brand & Style

The design system is centered on the concept of "Guided Serenity." It balances professional clinical excellence with the warmth of a modern wellness sanctuary. The target audience includes individuals seeking psychological support and holistic health services in Igarapava, requiring an interface that feels both deeply personal and impeccably organized.

The visual style is a blend of **Soft Minimalism** and **Organic Professionalism**. It prioritizes heavy whitespace to reduce cognitive load, utilizing translucent layers and soft-focus elements to evoke a sense of mental clarity. The emotional response should be one of immediate relief, safety, and modern accessibility, intentionally distancing itself from sterile, high-contrast medical environments.

## Colors

The palette is anchored by **Lavender (#967BB6)**, chosen for its psychological associations with tranquility and healing. 

- **Primary (Lavender):** Used for primary actions and brand emphasis.
- **Secondary (Lilac):** Utilized for backgrounds, decorative shapes, and soft highlights.
- **Tertiary (Gold):** Reserved exclusively for delicate accents, such as small icons, borders on featured items, or active indicators to convey "Qualité" (Quality).
- **Neutral (Soft Gray/Off-White):** Provides the structural canvas, ensuring the UI feels airy and expansive.
- **Success/Warning/Error:** Use desaturated versions of green and red to maintain the soft aesthetic without losing functional clarity.

## Typography

Typography plays a critical role in establishing a "friendly professional" tone. 

**Quicksand** is used for all headings. Its rounded terminals mirror the soft shapes of the UI, making titles appear approachable and less formal. **Be Vietnam Pro** is selected for body text and labels due to its contemporary feel and exceptional legibility at smaller sizes. 

For information-heavy sections, ensure a generous line height (minimum 1.5x) to prevent the text from feeling overwhelming to users who may be in a stressed state.

## Layout & Spacing

This design system employs a **Fluid Grid** with intentional "Breathing Zones." 

- **Desktop:** 12-column grid with 24px gutters and wide 80px side margins to center the focus.
- **Tablet:** 8-column grid with 24px margins.
- **Mobile:** 4-column grid with 16px margins.

Spacing follows a linear 8px scale. To maintain the "Minimalist" aesthetic, prioritize the `lg` (48px) and `xl` (80px) tokens for vertical section spacing. Content should never feel cramped; if in doubt, increase the whitespace.

## Elevation & Depth

Hierarchy is established through **Ambient Shadows** and **Tonal Layers** rather than harsh borders.

- **Surface Levels:** Use a pure white (`#FFFFFF`) for the primary interaction cards over an off-white (`#F9F9FB`) background.
- **Shadows:** Use extremely diffused, low-opacity shadows. For example: `0px 10px 30px rgba(150, 123, 182, 0.08)`. The shadow should have a slight lavender tint to harmonize with the primary color.
- **Blur:** Apply a subtle backdrop blur (10px) on navigation bars and floating overlays to create a sense of lightness and transparency.

## Shapes

The shape language is dominated by **Pill-shapes** and **Large Radii**. 

Avoid sharp 90-degree corners entirely. All primary containers and cards should use at least a 24px (`rounded-xl`) radius. This softness reduces the "clinical" feel and makes the interface feel safer and more inviting. Icons should follow this logic, using rounded stroke caps and joints.

## Components

- **Buttons:** Use a full-pill shape. Primary buttons feature a Lavender-to-Lilac subtle gradient. Text inside buttons should be semi-bold.
- **Cards:** Cards should have no visible border, relying on the ambient lavender-tinted shadow for definition. Add a 4px left-border accent in Gold for "Featured" or "Important" cards.
- **Input Fields:** Use a light gray background (`#F1F1F5`) with a 16px border-radius. On focus, the background turns white and gains a thin Lavender stroke.
- **Chips:** Used for medical specialties or tags. These should be light lilac with lavender text, fully rounded.
- **Navigation:** A minimalist top bar with high transparency and a blur effect. Links use Quicksand Medium with a soft dot indicator for the active state.
- **Lists:** Use generous vertical padding (16px+) and soft dividers (1px, 5% opacity black) that do not touch the edges of the container.