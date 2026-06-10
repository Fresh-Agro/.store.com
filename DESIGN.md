---
name: Fresh Agro Ecosystem
colors:
  surface: '#fcf9f8'
  surface-dim: '#dcd9d9'
  surface-bright: '#fcf9f8'
  surface-container-lowest: '#ffffff'
  surface-container-low: '#f6f3f2'
  surface-container: '#f0eded'
  surface-container-high: '#eae7e7'
  surface-container-highest: '#e5e2e1'
  on-surface: '#1b1c1c'
  on-surface-variant: '#40493d'
  inverse-surface: '#303030'
  inverse-on-surface: '#f3f0ef'
  outline: '#707a6c'
  outline-variant: '#bfcaba'
  surface-tint: '#1b6d24'
  primary: '#0d631b'
  on-primary: '#ffffff'
  primary-container: '#2e7d32'
  on-primary-container: '#cbffc2'
  inverse-primary: '#88d982'
  secondary: '#8b5000'
  on-secondary: '#ffffff'
  secondary-container: '#ff9800'
  on-secondary-container: '#653900'
  tertiary: '#923357'
  on-tertiary: '#ffffff'
  tertiary-container: '#b14b6f'
  on-tertiary-container: '#ffedf0'
  error: '#ba1a1a'
  on-error: '#ffffff'
  error-container: '#ffdad6'
  on-error-container: '#93000a'
  primary-fixed: '#a3f69c'
  primary-fixed-dim: '#88d982'
  on-primary-fixed: '#002204'
  on-primary-fixed-variant: '#005312'
  secondary-fixed: '#ffdcbe'
  secondary-fixed-dim: '#ffb870'
  on-secondary-fixed: '#2c1600'
  on-secondary-fixed-variant: '#693c00'
  tertiary-fixed: '#ffd9e2'
  tertiary-fixed-dim: '#ffb1c7'
  on-tertiary-fixed: '#3f001c'
  on-tertiary-fixed-variant: '#7f2448'
  background: '#fcf9f8'
  on-background: '#1b1c1c'
  surface-variant: '#e5e2e1'
  surface-alt: '#F5F5F5'
  border-subtle: '#E0E0E0'
  success-green: '#2E7D32'
  warning-orange: '#FF9800'
  bengali-text: '#424242'
typography:
  headline-xl:
    fontFamily: Inter
    fontSize: 40px
    fontWeight: '700'
    lineHeight: 48px
    letterSpacing: -0.02em
  headline-xl-mobile:
    fontFamily: Inter
    fontSize: 32px
    fontWeight: '700'
    lineHeight: 40px
  headline-lg:
    fontFamily: Inter
    fontSize: 28px
    fontWeight: '600'
    lineHeight: 36px
  headline-md:
    fontFamily: Inter
    fontSize: 20px
    fontWeight: '600'
    lineHeight: 28px
  body-lg:
    fontFamily: Inter
    fontSize: 18px
    fontWeight: '400'
    lineHeight: 28px
  body-md:
    fontFamily: Inter
    fontSize: 16px
    fontWeight: '400'
    lineHeight: 24px
  label-md:
    fontFamily: Inter
    fontSize: 14px
    fontWeight: '500'
    lineHeight: 20px
  label-sm:
    fontFamily: Inter
    fontSize: 12px
    fontWeight: '600'
    lineHeight: 16px
rounded:
  sm: 0.25rem
  DEFAULT: 0.5rem
  md: 0.75rem
  lg: 1rem
  xl: 1.5rem
  full: 9999px
spacing:
  container-max-width: 1280px
  gutter: 24px
  margin-mobile: 16px
  margin-desktop: 32px
  unit: 8px
---

## Brand & Style

The design system is centered on trust, freshness, and the "farm-to-table" connection essential for a premium Bangladeshi agro-commerce platform. It balances the vitality of agriculture with the efficiency of modern e-commerce.

The design style is **Corporate Modern with a Tactile Twist**. It leverages a structured grid and high-quality photography to convey professionalism, while subtle organic curves and vibrant accents ensure the experience feels approachable and appetizing. The interface remains intentionally clean to let the natural colors of fresh produce act as the primary visual driver.

## Colors

The palette is rooted in the natural world. **Fresh Leaf Green** serves as the primary brand anchor, used for headers, primary actions, and category indicators to reinforce the agro-identity. **Vibrant Orange** is reserved strictly for high-conversion moments, such as "Add to Cart" buttons and promotional badges, creating a clear visual hierarchy.

The background system uses a tiered approach: pure white for the primary canvas to ensure product photos pop, and a light gray for secondary content blocks and section dividers. Deep Charcoal is used for all English and Bengali typography to ensure AA accessibility and maximum legibility against light backgrounds.

## Typography

This design system utilizes **Inter** for its neutral, highly legible characteristics in digital interfaces. For Bengali script requirements, the system defaults to **Hind Siliguri** (or a system-standard sans-serif equivalent) to ensure vertical metrics remain consistent with the Latin characters.

- **Headlines:** Use Bold or Semi-Bold weights with tighter letter spacing for a premium, authoritative look.
- **Body Text:** Standardized at 16px for optimal reading comfort.
- **Bengali Support:** Line-heights for Bengali script should be increased by approximately 10-15% compared to Latin-only strings to accommodate vowel signs (kar/matra) without clipping.

## Layout & Spacing

The system employs a **12-column fixed grid** for desktop and a **4-column fluid grid** for mobile. 

- **Vertical Rhythm:** Built on an 8px base unit. All paddings, margins, and component heights must be multiples of 8px (e.g., 16px, 24px, 32px).
- **Desktop:** 1280px max-width container, centered. Gutters are fixed at 24px.
- **Mobile:** Full-width layout with 16px side margins. 
- **Reflow:** On tablet/mobile, product grids transition from 4-5 items per row to 2 items per row to maintain image clarity.

## Elevation & Depth

Visual hierarchy is established through **Tonal Layers** rather than heavy shadows, reflecting a clean, modern agro-aesthetic.

- **Level 0 (Base):** Light Gray (#F5F5F5) background for the main body area.
- **Level 1 (Cards):** White (#FFFFFF) surfaces with a 1px border (#E0E0E0). No shadow. This is used for product cards in a grid.
- **Level 2 (Interaction):** When hovered, cards or buttons may gain a very soft, diffused shadow (12% opacity, 8px blur) to indicate interactivity.
- **Level 3 (Overlays):** Sticky navigation, mini-carts, and modals use a crisp, low-contrast outline combined with a medium-diffusion shadow to separate them from the content beneath.

## Shapes

The design system uses a **Rounded** shape language to evoke a friendly, trustworthy feel. 

- **Product Cards & Containers:** Use 8px (`rounded`) to 12px (`rounded-lg`) corner radii.
- **Input Fields:** Search bars and text inputs should use 8px roundedness for a modern, structured look.
- **CTA Buttons:** Primary buttons use 8px corners. Secondary "pill" labels or chips may use a full radius for distinct visual categorization.

## Components

- **Buttons:** 
    - **Primary:** Fresh Leaf Green background, white text. 
    - **CTA:** Vibrant Orange background, white text. Bold weight.
    - **Secondary:** Outlined green with 1.5px border.
- **Search Bar:** Prominent, centered in the header. Large hit area (min-height 48px), 8px rounded corners, with a dedicated "Location Selector" dropdown integrated into the left side.
- **Product Cards:** Minimalist design. High-quality image on a white background, 1px subtle border, 8px rounded corners. Price in Deep Charcoal (Bold), unit (e.g., "per kg") in 12px gray text.
- **Mini-Cart:** Sticky floating action button or sidebar. Uses a Vibrant Orange badge for item counts to draw immediate attention.
- **Location Selector:** Clearly visible in the top navigation bar, using a pin icon and a chevron to indicate a menu for area selection (e.g., "Dhanmondi, Dhaka").
- **Chips:** Used for "Organic," "Discount," or "New" badges. 4px roundedness, placed at the top-left of product images.