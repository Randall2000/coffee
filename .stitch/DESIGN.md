---
name: Barista Flow
colors:
  surface: '#fafafa'
  surface-dim: '#f5f5f5'
  surface-bright: '#ffffff'
  surface-container-lowest: '#ffffff'
  surface-container-low: '#fafafa'
  surface-container: '#f5f5f5'
  surface-container-high: '#e5e5e5'
  surface-container-highest: '#d4d4d4'
  on-surface: '#171717'
  on-surface-variant: '#525252'
  outline: '#e5e5e5'
  outline-variant: '#f5f5f5'
  primary: '#d97706'
  on-primary: '#ffffff'
  primary-container: '#fffbeb'
  on-primary-container: '#92400e'
  primary-dim: '#f59e0b'
  primary-bright: '#b45309'
  secondary: '#a3a3a3'
  on-secondary: '#ffffff'
  secondary-container: '#f5f5f5'
  on-secondary-container: '#404040'
  error: '#dc2626'
  on-error: '#ffffff'
  error-container: '#fef2f2'
  on-error-container: '#991b1b'
  background: '#fafafa'
  on-background: '#171717'
  surface-variant: '#fef3c7'
  desktop-gradient-start: '#fef3c7'
  desktop-gradient-mid: '#fde68a'
  desktop-gradient-end: '#fef9ee'
typography:
  display-lg:
    fontFamily: system-ui, -apple-system, sans-serif
    fontSize: 42px
    fontWeight: '900'
    lineHeight: 48px
    letterSpacing: -0.02em
  headline-md:
    fontFamily: system-ui, -apple-system, sans-serif
    fontSize: 28px
    fontWeight: '700'
    lineHeight: 34px
    letterSpacing: -0.01em
  title-base:
    fontFamily: system-ui, -apple-system, sans-serif
    fontSize: 16px
    fontWeight: '700'
    lineHeight: 24px
    letterSpacing: '0'
  body-sm:
    fontFamily: system-ui, -apple-system, sans-serif
    fontSize: 14px
    fontWeight: '400'
    lineHeight: 20px
    letterSpacing: '0'
  label-caps:
    fontFamily: system-ui, -apple-system, sans-serif
    fontSize: 10px
    fontWeight: '700'
    lineHeight: 16px
    letterSpacing: 0.1em
  stat-mono:
    fontFamily: ui-monospace, monospace
    fontSize: 18px
    fontWeight: '700'
    lineHeight: 24px
    letterSpacing: '0'
rounded:
  sm: 0.5rem
  DEFAULT: 0.75rem
  md: 0.75rem
  lg: 1rem
  xl: 1.5rem
  full: 9999px
  sheet-top: 1.5rem
spacing:
  unit: 4px
  xs: 4px
  sm: 8px
  md: 16px
  lg: 20px
  xl: 24px
  gutter: 16px
  margin-mobile: 20px
  section: 12px
---

## Brand & Style

Barista Flow is a focused, single-task mobile app for pour-over coffee. The visual language is **warm minimalism** — clean white surfaces accented by a rich amber that evokes roasted beans and handcrafted warmth. Every screen strips away distraction to surface the numbers that matter: grams, millilitres, temperature, time. The palette is intentionally restraintful — one strong accent colour on a quietly textured neutral ground.

The app behaves and feels like a native iOS utility. Interactions are spring-physics-based, sheets slide from the bottom with momentum, and touch targets are generous. The typography leans heavily on bold weights and monospaced numerals to make brew parameters scannable at a glance — the user may have wet hands and no patience for visual noise.

## Colors

The palette is built on **two anchors**: warm white/neutral for surfaces and **Amber 600 (#d97706)** as the sole brand accent. Amber carries all interactive meaning — primary buttons, active states, icons, badges — while neutrals handle structure and hierarchy.

**Primary Foundation**
- **Parchment White** `#ffffff` — card surfaces, modals, sheets
- **Warm Mist** `#fafafa` — page background (neutral-50)
- **Light Ash** `#f5f5f5` — secondary surfaces, disabled states, stat cell backgrounds (neutral-100)
- **Silver Edge** `#e5e5e5` — borders, dividers (neutral-200)

**Accent & Interactive**
- **Barista Amber** `#d97706` — primary CTA buttons, active icons, star ratings, progress (amber-600)
- **Soft Amber** `#f59e0b` — arc/ring fills, in-progress indicators (amber-500)
- **Deep Amber** `#b45309` — hover/pressed state for primary amber (amber-700)
- **Amber Blush** `#fffbeb` — amber tint backgrounds, chip fills (amber-50)
- **Amber Haze** `#fef3c7` — subtle amber-tinted surface, desktop background (amber-100)

**Typography & Text Hierarchy**
- **Ink** `#171717` — primary text, headings (neutral-900)
- **Graphite** `#262626` — card titles, stat values (neutral-800)
- **Stone** `#525252` — body text, secondary labels (neutral-600 / on-surface-variant)
- **Slate** `#737373` — tertiary, metadata (neutral-500)
- **Fog** `#a3a3a3` — placeholder, disabled text (neutral-400)
- **Mist** `#d4d4d4` — empty stars, decorative dividers (neutral-300)

**Functional States**
- **Alert Red** `#dc2626` — delete/destructive actions, error states (red-600)
- **Red Blush** `#fef2f2` — destructive action hover backgrounds (red-50)

## Typography

The app uses the system font stack (`system-ui, -apple-system`) everywhere. This is a deliberate choice — it ensures the app looks native on each platform without loading external fonts.

**Hierarchy & Weights**
- **Display (timer circle centre)** — 42px / black (900) / tight tracking: the brew-time countdown needs to be readable across the room
- **Stat values (grams, ml, °C)** — 28px or 18px / bold (700) / monospaced: all numeric data uses `font-mono tabular-nums` to prevent layout shift as digits change
- **Card titles / screen headings** — 16px–18px / bold (700)
- **Body / list items** — 14px / medium (500) or regular (400)
- **Section labels** — 10px–11px / bold (700) / `tracking-widest` / `uppercase`: used as section headers above groups of settings ("GRINDING", "PREPARATION")
- **Badges / chips** — 10px–12px / bold (700) / `rounded-full`

**Spacing Principles**
- Line height: `leading-tight` (1.25) for display and card titles; `leading-none` for stats inside cells
- Letter-spacing: `tracking-widest` only on uppercase section labels; body text uses default
- Monospace exclusively for numbers that change (timer, grams, ml) — never for labels

## Component Stylings

### Buttons

**Primary (CTA):** Full-width, `bg-amber-600 text-white`, `rounded-xl` (12px), `font-bold`, min-height 44px (h-11 or `py-4`). Drop shadow: `shadow-xl shadow-amber-200/60` — a warm amber glow underneath. Press state: `active:scale-[0.98]`. No icon unless needed for clarity.

**Secondary / Toggle button:** `bg-amber-50 text-amber-700 border border-amber-200`, same radius and height. Used for "調整參數" and similar expandable actions.

**Ghost / Back:** `bg-white border border-neutral-200 text-neutral-400`, `w-9 h-9 rounded-xl`, icon-only. Used for navigation back.

**Destructive:** Red trash icon only — no text label. Accessed from inside the bottom sheet, never on the card directly.

### Cards & Journal Containers

**Journal Log Card:** `bg-white rounded-2xl border border-neutral-100 shadow-sm overflow-hidden`. Tap to open detail bottom sheet. Internal layout: top section `p-4 pb-3` with title + star rating row; pill badge row `px-4 pb-3`; optional italic notes `px-4 py-2.5 border-t border-neutral-50 bg-neutral-50`. No action buttons on the card surface.

**Stats Summary Card (brew confirmation):** Same white card treatment with three stat cells in a 3-column grid. Each cell: `bg-neutral-50 rounded-xl py-3` with large bold number + small uppercase label.

**Brew Timer Card (arc display):** Full-height immersive view. Dark amber arc on SVG ring, centre shows current step name + countdown. No card border — fills the screen.

### Navigation

**Bottom Tab Bar:** `bg-white border-t border-neutral-100`. Two items max (沖煮 / 日誌). Each tab: icon + text label, amber fill when active, neutral-400 when inactive. Safe area bottom padding applied via `env(safe-area-inset-bottom)`. `z-50` to float above content.

**Step progress indicator (brew flow):** Two amber pills in top-right corner showing current step (1-of-2, 2-of-2).

### Bottom Sheets

Slide up from bottom. `bg-white rounded-t-3xl` (24px top radius). Shadow: `0 -4px 24px rgba(0,0,0,0.10)`. Drag handle pill: `w-10 h-1 rounded-full bg-neutral-200` centered at top. Open animation: `0.42s cubic-bezier(0.32, 0.72, 0, 1)` (spring). Dismiss animation: `0.32s cubic-bezier(0.4, 0, 1, 1)` (fast decelerate off-screen). Backdrop: `bg-black/50` with `0.28s` fade.

### Inputs & Forms

Input fields: `bg-neutral-50 rounded-xl border border-neutral-200 text-sm`, focus ring: `ring-2 ring-amber-500`. Font-size 16px enforced to prevent iOS auto-zoom. Stepper buttons (±): `w-9 h-9 rounded-xl bg-white border border-neutral-200`, `active:scale-95`.

### Radar Chart (Flavor Profile)

Custom SVG pentagon. Five axes (酸感/甜感/苦味/醇厚 + one more). Filled polygon: amber at 20% opacity. Vertex dots: `fill-amber-600`. Labels positioned at each axis tip. Drag interaction for real-time adjustment.

### Chips & Badges

**Recipe badge:** `rounded-full bg-amber-50 px-2.5 py-1 text-xs font-semibold text-amber-700`  
**Roast level badge:** Small coloured pill (`rounded font-medium` with roast-specific tint classes)  
**Section count badge:** `bg-amber-50 border border-amber-100 rounded-lg px-2 py-1 text-xs font-mono text-amber-700`  
**"建議" (recommended) badge:** `rounded-full bg-amber-100 px-2 py-0.5 text-[10px] font-bold text-amber-700`

## Layout Principles

### Grid & Structure

Single-column mobile-first layout. On desktop (≥640px), the entire app renders as a 390×844px phone frame, centred on a warm amber gradient (`#fef3c7 → #fde68a → #fef9ee`). The frame has `border-radius: 44px` and a layered box-shadow simulating a physical device.

No grid system — all layouts use vertical stack (`space-y-3`, `space-y-4`) inside a scrollable content area.

### Whitespace Strategy

Base unit: 4px. Common rhythm: 8px (gap-2), 12px (gap-3 / py-3), 16px (px-4), 20px (px-5). Content padding inside cards: `p-4` (16px). Section gaps between cards: `space-y-3` (12px). Page padding: `px-5 py-5` (20px).

The spacing feels snug but intentional — dense enough for data utility, airy enough to avoid crowding. Section labels (10px ALL-CAPS) create clear visual breaks without needing extra spacing.

### Alignment & Visual Balance

All text is left-aligned. Stars and metadata align right inside card header rows (`flex items-start justify-between`). Numeric stat cells centre their content. The timer circle is fully centred on screen.

### Responsive Behavior & Touch

Mobile-first. Touch targets minimum 44×44px (enforced on all interactive buttons). `touch-action: manipulation` on `body` eliminates 300ms tap delay. `overscroll-behavior: contain` prevents pull-to-refresh conflicts. Bottom sheet drag threshold prevents accidental dismissals.

## Design System Notes for Stitch Generation

### Language to Use
- "warm amber minimal", "coffee barista aesthetic", "clean white cards on neutral background"
- "mobile utility app", "single-column", "bottom sheet navigation"
- "bold numeric stats", "monospaced data", "soft amber glow CTA"
- "roasted warm tones", "handcrafted precision", "tactile spring animations"

### Color References
- Brand amber: `#d97706` (amber-600)
- Amber pressed: `#b45309` (amber-700)
- Amber tint bg: `#fffbeb` (amber-50)
- Page background: `#fafafa` (neutral-50)
- Card surface: `#ffffff`
- Border: `#f5f5f5` to `#e5e5e5` (neutral-100 / neutral-200)
- Primary text: `#262626` (neutral-800)
- Secondary text: `#a3a3a3` (neutral-400)

### Component Prompts
- "A journal log card showing bean name, date, roast badge, recipe chip, and star rating. White card, rounded-2xl, subtle border, tap to expand."
- "A brew timer screen with a large amber arc circle in the centre, step name and countdown in the middle, progress bar below the header."
- "A bottom sheet with drag handle, title, and a list of selectable options. Spring slide-up animation from bottom of screen."
- "Three stat cells in a row showing grams, ml, and temperature. Each cell has a large bold monospaced number and a small uppercase label underneath."

### Incremental Iteration
- Start screens with `bg-neutral-50` page background and `bg-white rounded-2xl border border-neutral-100` cards
- Use `text-amber-600` for all interactive accent elements
- For CTA buttons, always use `bg-amber-600 text-white rounded-xl font-bold` with amber glow shadow
- Section labels should always be `text-[10px] font-bold text-neutral-400 uppercase tracking-widest`
- Numeric data should always use `font-mono tabular-nums font-bold`
