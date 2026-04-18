# Hero Section — Visual & Typography Breakdown
*Kingdom Para Para · Breakdance Builder Reference*

---

## Section Container

| Property | Value |
|---|---|
| Background colour | `#EDECE9` — Stone/Parchment |
| Min-height | `100dvh` (full dynamic viewport height) |
| Display | Flex, vertically centred |
| Overflow | Hidden |

```css
/* ─────────────────────────────────────────
   HERO — Section Container
───────────────────────────────────────── */
#hero {
  position: relative;
  min-height: 100dvh;
  background-color: #EDECE9;
  overflow: hidden;
  display: flex;
  align-items: center;
}
```

---

## Background Texture Layer

A photographic texture sits behind all content to add depth without competing.

| Property | Value |
|---|---|
| Image | `Terracotta Walls and Pots.webp` |
| Position | Absolute, fills entire section |
| Sizing | Cover / Centre |
| Opacity | `5%` — extremely subtle, barely perceptible |

```css
/* ─────────────────────────────────────────
   HERO — Background Texture
───────────────────────────────────────── */
.hero-bg-texture {
  position: absolute;
  inset: 0;
  background-image: url('YOUR_IMAGE_PATH/Terracotta Walls and Pots.webp');
  background-size: cover;
  background-position: center;
  opacity: 0.05;
  pointer-events: none;
}
```

---

## Layout Grid

| Property | Value |
|---|---|
| Max-width | `1280px` |
| Horizontal padding | `24px` (both sides) |
| Padding top | `144px` mobile / `160px` desktop |
| Padding bottom | `96px` mobile / `112px` desktop |
| Columns | 1 column mobile / 2 columns desktop (`1.2fr : 1fr`) |
| Column gap | `40px` mobile / `64px` desktop |
| Alignment | Items vertically centred |

```css
/* ─────────────────────────────────────────
   HERO — Layout Grid
───────────────────────────────────────── */
.hero-grid {
  position: relative;
  width: 100%;
  max-width: 1280px;
  margin: 0 auto;
  padding: 144px 24px 96px;
  display: grid;
  grid-template-columns: 1fr;
  gap: 40px;
  align-items: center;
}

@media (min-width: 768px) {
  .hero-grid {
    grid-template-columns: 1.2fr 1fr;
    gap: 64px;
    padding: 160px 24px 112px;
  }
}
```

---

## Element 01 — Eyebrow Tag

> "Welcome to Kingdom Para Para"

| Property | Value |
|---|---|
| Font family | Plus Jakarta Sans |
| Font weight | Light (300) |
| Font size | `0.625rem` — **10px** |
| Text transform | Uppercase |
| Letter spacing | `0.2em` |
| Text colour | `rgba(11, 35, 75, 0.75)` — Navy at 75% opacity |
| Background | `rgba(11, 35, 75, 0.05)` — Navy at 5% opacity |
| Border | `1px solid rgba(11, 35, 75, 0.14)` |
| Border radius | `9999px` — full pill shape |
| Padding | `5.6px` top & bottom / `14.4px` left & right |
| Display | Inline-flex |

```css
/* ─────────────────────────────────────────
   HERO — Element 01: Eyebrow Tag
───────────────────────────────────────── */
.hero-eyebrow {
  display: inline-flex;
  align-items: center;
  font-family: 'Plus Jakarta Sans', system-ui, sans-serif;
  font-weight: 300;
  font-size: 0.625rem;        /* 10px */
  text-transform: uppercase;
  letter-spacing: 0.2em;
  padding: 0.35rem 0.9rem;    /* 5.6px top/bottom · 14.4px left/right */
  border-radius: 9999px;
  border: 1px solid rgba(11, 35, 75, 0.14);
  color: rgba(11, 35, 75, 0.75);
  background-color: rgba(11, 35, 75, 0.05);
}
```

---

## Element 02 — H1 Heading

> Line 1: "Your heart is a treasure chest."
> Line 2 (dimmed): "It is time to unlock what God placed inside."

| Property | Value |
|---|---|
| Font family | Oranienbaum |
| Font weight | Regular (400) |
| Font size | `clamp(2.75rem, 6vw, 4.5rem)` — **min 44px → max 72px** |
| Line height | `1.06` |
| Letter spacing | `-0.025em` (tight) |
| Colour — line 1 | `#0B234B` — Navy at full opacity |
| Colour — line 2 | `rgba(11, 35, 75, 0.72)` — Navy at 72% opacity |
| Margin top | `28px` from eyebrow tag |

> **Breakdance note:** The second line requires a separate inline `<span>` with reduced opacity. Wrap it in a span and apply the `.hero-h1-dim` class below.

```css
/* ─────────────────────────────────────────
   HERO — Element 02: H1 Heading
───────────────────────────────────────── */
.hero-h1 {
  font-family: 'Oranienbaum', Georgia, serif;
  font-weight: 400;
  font-size: clamp(2.75rem, 6vw, 4.5rem); /* min 44px → max 72px */
  line-height: 1.06;
  letter-spacing: -0.025em;
  color: #0B234B;
  margin-top: 1.75rem;        /* 28px */
}

/* Dimmed second line — wrap in a <span> */
.hero-h1 .hero-h1-dim {
  opacity: 0.72;
}
```

---

## Element 03 — Body Paragraph

> "You were created to walk in intimacy with Jesus and fullness of purpose…"

| Property | Value |
|---|---|
| Font family | Plus Jakarta Sans |
| Font weight | Light (300) |
| Font size | `1.0625rem` — **17px** |
| Line height | `1.625` (relaxed) |
| Colour | `rgba(11, 35, 75, 0.60)` — Navy at 60% opacity |
| Max-width | `52ch` — approximately 52 characters per line |
| Margin top | `28px` from heading |

```css
/* ─────────────────────────────────────────
   HERO — Element 03: Body Paragraph
───────────────────────────────────────── */
.hero-body {
  font-family: 'Plus Jakarta Sans', system-ui, sans-serif;
  font-weight: 300;
  font-size: 1.0625rem;       /* 17px */
  line-height: 1.625;
  color: rgba(11, 35, 75, 0.60);
  max-width: 52ch;
  margin-top: 1.75rem;        /* 28px */
}
```

---

## Element 04 — CTA Button (Gold)

> "Unlock the Treasure Within →"

| Property | Value |
|---|---|
| Font family | Plus Jakarta Sans |
| Font weight | Light (300) |
| Font size | `0.8125rem` — **13px** |
| Letter spacing | `0.025em` |
| Text colour | `#ffffff` — White |
| Background colour | `#BF8B19` — Yellow Gold |
| Background colour (hover) | `#a57816` — Darker Gold |
| Border radius | `9999px` — full pill |
| Padding | `14.4px` top & bottom / `25.6px` left & right |
| Margin top | `40px` from paragraph |
| Hover transform | `translateY(-1px)` — slight lift |

### Arrow Icon Ring (inside the button)
| Property | Value |
|---|---|
| Size | `30px × 30px` |
| Shape | Circle |
| Background | `rgba(255, 255, 255, 0.18)` — semi-transparent white |
| Icon | `→` arrow character |
| Icon size | `14px` |
| Gap from button text | `11.2px` |
| Hover transform | `translate(2px, -1px)` |

```css
/* ─────────────────────────────────────────
   HERO — Element 04: CTA Button (Gold)
───────────────────────────────────────── */
.hero-btn-gold {
  display: inline-flex;
  align-items: center;
  gap: 0.7rem;                /* 11.2px between text and icon */
  background-color: #BF8B19;
  color: #ffffff;
  font-family: 'Plus Jakarta Sans', system-ui, sans-serif;
  font-weight: 300;
  font-size: 0.8125rem;       /* 13px */
  letter-spacing: 0.025em;
  padding: 0.9rem 1.6rem;     /* 14.4px top/bottom · 25.6px left/right */
  border-radius: 9999px;
  text-decoration: none;
  border: none;
  cursor: pointer;
  margin-top: 2.5rem;         /* 40px */
  transition: background-color 0.45s cubic-bezier(0.32, 0.72, 0, 1),
              transform 0.3s cubic-bezier(0.32, 0.72, 0, 1);
}

.hero-btn-gold:hover {
  background-color: #a57816;
  transform: translateY(-1px);
}

.hero-btn-gold:active {
  transform: scale(0.975);
}

/* Icon ring inside the button */
.hero-btn-gold .icon-ring {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 1.875rem;            /* 30px */
  height: 1.875rem;           /* 30px */
  border-radius: 9999px;
  background-color: rgba(255, 255, 255, 0.18);
  font-size: 0.875rem;        /* 14px */
  line-height: 1;
  transition: transform 0.3s cubic-bezier(0.32, 0.72, 0, 1);
}

.hero-btn-gold:hover .icon-ring {
  transform: translate(2px, -1px);
}
```

---

## Element 05 — Main Hero Image

| Property | Value |
|---|---|
| Image file | `Treasure Chest in the Sand.webp` |
| Aspect ratio | `3:4` — portrait orientation |
| Object-fit | Cover, centred |
| Width | 100% of its column |

### Bezel Frame — Outer Layer
| Property | Value |
|---|---|
| Background | `rgba(11, 35, 75, 0.04)` — very faint Navy tint |
| Border | `1px solid rgba(11, 35, 75, 0.09)` |
| Padding | `7px` on all sides |
| Border radius | `32px` — large rounded corners |

### Bezel Core — Inner Layer (clips the image)
| Property | Value |
|---|---|
| Border radius | `25px` (32px outer − 7px padding) |
| Overflow | Hidden |

```css
/* ─────────────────────────────────────────
   HERO — Element 05: Main Hero Image
───────────────────────────────────────── */

/* Outer bezel frame */
.hero-image-bezel {
  background-color: rgba(11, 35, 75, 0.04);
  border: 1px solid rgba(11, 35, 75, 0.09);
  padding: 7px;
  border-radius: 32px;        /* 2rem */
}

/* Inner layer — clips image to rounded shape */
.hero-image-bezel-core {
  border-radius: 25px;        /* 32px outer − 7px padding */
  overflow: hidden;
}

/* The image itself */
.hero-image-bezel-core img {
  width: 100%;
  display: block;
  object-fit: cover;
  object-position: center;
  aspect-ratio: 3 / 4;
}
```

---

## Element 06 — Accent Thumbnail (Desktop Only)

> Small secondary image overlapping the bottom-left corner of the main image.

| Property | Value |
|---|---|
| Image file | `Clay Pots by Wall.webp` |
| Size | `96px × 96px` |
| Position | Absolute — `−20px` from bottom, `−20px` from left |
| Visibility | Hidden on mobile / shown at `768px+` |
| Bezel treatment | Identical to main image bezel |

```css
/* ─────────────────────────────────────────
   HERO — Element 06: Accent Thumbnail
───────────────────────────────────────── */

/* Wrapper — the image column must be position: relative */
.hero-image-col {
  position: relative;
}

/* Thumbnail — hidden on mobile */
.hero-accent-thumb {
  display: none;
  position: absolute;
  bottom: -20px;              /* -bottom-5 */
  left: -20px;                /* -left-5  */
  width: 96px;                /* w-24 */
  height: 96px;               /* h-24 */
  background-color: rgba(11, 35, 75, 0.04);
  border: 1px solid rgba(11, 35, 75, 0.09);
  padding: 7px;
  border-radius: 32px;
}

/* Show from tablet up */
@media (min-width: 768px) {
  .hero-accent-thumb {
    display: block;
  }
}

/* Inner clip layer */
.hero-accent-thumb-core {
  border-radius: 25px;
  overflow: hidden;
  height: 100%;
}

.hero-accent-thumb-core img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  display: block;
}
```

---

## Global Layer — Film Grain Overlay

Sits over the entire page at all times, adds analogue texture.

| Property | Value |
|---|---|
| Type | SVG fractal noise (`feTurbulence`) |
| Tile size | `300px × 300px` |
| Opacity | `0.022` — ~2% |
| Z-index | `200` |
| Pointer-events | None |

```css
/* ─────────────────────────────────────────
   GLOBAL — Film Grain Overlay
   (applies to the whole page, not just hero)
───────────────────────────────────────── */
#grain {
  position: fixed;
  inset: 0;
  top: 0; right: 0; bottom: 0; left: 0; /* fallback for older builders */
  z-index: 200;
  pointer-events: none;
  opacity: 0.022;
  background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='300' height='300'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.85' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='300' height='300' filter='url(%23n)'/%3E%3C/svg%3E");
  background-size: 300px 300px;
}
```

---

## Animation System — Scroll Reveal

All hero elements animate in from below when they enter the viewport.

| Property | Value |
|---|---|
| Initial state | `opacity: 0` / `translateY: 28px` |
| Final state | `opacity: 1` / `translateY: 0` |
| Duration | `0.85s` |
| Easing | `cubic-bezier(0.32, 0.72, 0, 1)` — ease-out |
| Trigger | IntersectionObserver at 8% element visibility |

### Stagger Delays

| Element | Delay |
|---|---|
| Eyebrow tag | `0ms` — no delay |
| H1 Heading | `100ms` |
| Body paragraph | `200ms` |
| CTA Button | `300ms` |
| Hero image | `150ms` |
| Accent thumbnail | `400ms` |

```css
/* ─────────────────────────────────────────
   GLOBAL — Scroll Reveal Animation
───────────────────────────────────────── */

/* Hidden initial state */
.reveal {
  opacity: 0;
  transform: translateY(1.75rem);   /* 28px */
  transition: opacity 0.85s cubic-bezier(0.32, 0.72, 0, 1),
              transform 0.85s cubic-bezier(0.32, 0.72, 0, 1);
}

/* Visible state — added by JS when element enters viewport */
.reveal.is-visible {
  opacity: 1;
  transform: translateY(0);
}

/* Stagger delays — add data-delay attribute to each element */
.reveal[data-delay="100"] { transition-delay: 0.1s; }
.reveal[data-delay="150"] { transition-delay: 0.15s; }
.reveal[data-delay="200"] { transition-delay: 0.2s; }
.reveal[data-delay="300"] { transition-delay: 0.3s; }
.reveal[data-delay="400"] { transition-delay: 0.4s; }
```

> **Breakdance note:** Breakdance Builder has its own entrance animation system. You can either use that (set each element to fade + slide up, matching the values above) or paste the CSS above into Custom CSS and trigger the `.is-visible` class via a small JavaScript snippet in a Code Block element.

---

## Typography Summary

| Element | Font | Weight | Size | Colour |
|---|---|---|---|---|
| Eyebrow tag | Plus Jakarta Sans | Light 300 | 10px | Navy 75% |
| H1 — line 1 | Oranienbaum | Regular 400 | 44–72px (fluid) | Navy 100% |
| H1 — line 2 | Oranienbaum | Regular 400 | 44–72px (fluid) | Navy 72% |
| Body paragraph | Plus Jakarta Sans | Light 300 | 17px | Navy 60% |
| CTA button label | Plus Jakarta Sans | Light 300 | 13px | White |

---

## Colour Summary

| Swatch | HEX / Value | Usage in hero |
|---|---|---|
| Stone | `#EDECE9` | Section background |
| Navy | `#0B234B` | All text at full opacity |
| Yellow Gold | `#BF8B19` | CTA button background |
| Yellow Gold (hover) | `#a57816` | CTA button hover state |
| Navy 72% | `rgba(11, 35, 75, 0.72)` | H1 second line |
| Navy 60% | `rgba(11, 35, 75, 0.60)` | Body paragraph |
| Navy 14% | `rgba(11, 35, 75, 0.14)` | Eyebrow border |
| Navy 5% | `rgba(11, 35, 75, 0.05)` | Eyebrow background |
| Navy 9% | `rgba(11, 35, 75, 0.09)` | Bezel border |
| Navy 4% | `rgba(11, 35, 75, 0.04)` | Bezel background |
| White 18% | `rgba(255, 255, 255, 0.18)` | Icon ring inside button |

---

## Font Import (for Breakdance)

Add to **Global Styles → Custom CSS** or the site `<head>`:

```css
@import url('https://fonts.googleapis.com/css2?family=Oranienbaum&family=Newsreader:wght@300&family=Plus+Jakarta+Sans:wght@300;400&display=swap');
```
