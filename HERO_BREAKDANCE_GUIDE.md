# Hero Section — Breakdance Builder Step-by-Step Guide
*Kingdom Para Para · Free elements only · No Pro required*

---

## Before You Start

### Add your fonts
Go to **Breakdance → Global Styles → Custom CSS** and paste this at the very top. This loads all three brand fonts from Google Fonts and must be done once before anything else.

```css
@import url('https://fonts.googleapis.com/css2?family=Oranienbaum&family=Newsreader:ital,wght@0,300;1,300&family=Plus+Jakarta+Sans:wght@300;400&display=swap');
```

---

## Element Structure Overview

This is the nesting order you will build. Each numbered item is a separate Breakdance element. Add them in this exact order.

```
1. Section
└── 2. Columns
    ├── Left Column
    │   ├── 3. Div  ←  eyebrow tag
    │   │   └── 4. Text  ←  "Welcome to Kingdom Para Para"
    │   ├── 5. Heading  ←  H1
    │   ├── 6. Text  ←  body paragraph
    │   └── 7. Button  ←  CTA
    └── Right Column
        ├── 8. Div  ←  outer bezel frame
        │   └── 9. Div  ←  inner bezel core (clips image)
        │       └── 10. Image  ←  Treasure Chest in the Sand
        └── 11. Div  ←  accent thumbnail (absolute)
            └── 12. Div  ←  accent bezel core
                └── 13. Image  ←  Clay Pots by Wall
```

---

## Step 1 — Section

Add a **Section** element. This is the outermost wrapper for the entire hero.

**In the Breakdance panel, configure these settings:**

| Tab | Setting | Value |
|---|---|---|
| Layout | Min Height | `100dvh` |
| Background | Color | `#EDECE9` |
| Spacing | Padding | Set all padding to `0` — the inner Columns will handle spacing |

**Custom CSS** — paste this into the Section's Custom CSS field:

```css
%%SELECTOR%% {
  position: relative;
  overflow: hidden;
  display: flex;
  align-items: center;
}

/* Background texture overlay — sits at 5% opacity over the stone background */
%%SELECTOR%%::before {
  content: '';
  position: absolute;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  background-image: url('PASTE_YOUR_TEXTURE_IMAGE_URL_HERE');
  background-size: cover;
  background-position: center;
  opacity: 0.05;
  pointer-events: none;
  z-index: 0;
}
```

> Replace `PASTE_YOUR_TEXTURE_IMAGE_URL_HERE` with the WordPress media URL for **Terracotta Walls and Pots** after uploading it.

---

## Step 2 — Columns

Inside the Section, add a **Columns** element. This creates the two-column left/right layout.

**In the Breakdance panel, configure these settings:**

| Tab | Setting | Value |
|---|---|---|
| Layout | Columns | `2` |
| Layout | Left column width | `55%` |
| Layout | Right column width | `45%` |
| Layout | Gap | `40px` |
| Layout | Align Items | `Center` |

**Custom CSS** — paste this into the Columns element's Custom CSS field:

```css
%%SELECTOR%% {
  position: relative;
  z-index: 1;
  width: 100%;
  max-width: 1280px;
  margin: 0 auto;
  padding: 144px 24px 96px;
  box-sizing: border-box;
}

/* Desktop spacing and column ratio */
@media (min-width: 768px) {
  %%SELECTOR%% {
    padding: 160px 24px 112px;
    gap: 64px;
  }
}

/* Stack to a single column on mobile */
@media (max-width: 767px) {
  %%SELECTOR%% {
    grid-template-columns: 1fr !important;
    gap: 40px;
  }
}
```

---

## Step 3 — Div (Eyebrow Tag Wrapper)

Inside the **left column**, add a **Div** element. This becomes the pill-shaped tag around the eyebrow text.

**In the Breakdance panel:**

| Tab | Setting | Value |
|---|---|---|
| Layout | Display | `Inline Flex` |
| Layout | Align Items | `Center` |

**Custom CSS:**

```css
%%SELECTOR%% {
  display: inline-flex;
  align-items: center;
  font-family: 'Plus Jakarta Sans', system-ui, sans-serif;
  font-weight: 300;
  font-size: 0.625rem;        /* 10px */
  text-transform: uppercase;
  letter-spacing: 0.2em;
  padding: 0.35rem 0.9rem;
  border-radius: 9999px;
  border: 1px solid rgba(11, 35, 75, 0.14);
  color: rgba(11, 35, 75, 0.75);
  background-color: rgba(11, 35, 75, 0.05);
}
```

---

## Step 4 — Text (Eyebrow Label)

Inside the **Eyebrow Div** (Step 3), add a **Text** element.

**In the Breakdance panel:**

| Tab | Setting | Value |
|---|---|---|
| Content | Text | `Welcome to Kingdom Para Para` |

**Custom CSS:**

```css
%%SELECTOR%% {
  font-family: 'Plus Jakarta Sans', system-ui, sans-serif;
  font-weight: 300;
  font-size: 0.625rem;
  text-transform: uppercase;
  letter-spacing: 0.2em;
  color: rgba(11, 35, 75, 0.75);
  margin: 0;
  padding: 0;
  line-height: 1;
}
```

---

## Step 5 — Heading (H1)

Inside the **left column**, directly after the Eyebrow Div, add a **Heading** element.

**In the Breakdance panel:**

| Tab | Setting | Value |
|---|---|---|
| Content | Tag | `H1` |
| Content | Text | See below |
| Typography | Font Family | `Oranienbaum` |
| Typography | Font Weight | `Regular (400)` |
| Typography | Color | `#0B234B` |
| Spacing | Margin Top | `28px` |

**For the heading text**, switch to HTML mode in the content field and paste this exactly:

```html
Your heart is a treasure&nbsp;chest.<br>
<span class="h1-dim">It is time to unlock what God placed inside.</span>
```

**Custom CSS:**

```css
%%SELECTOR%% {
  font-family: 'Oranienbaum', Georgia, serif;
  font-weight: 400;
  font-size: clamp(2.75rem, 6vw, 4.5rem); /* scales from 44px to 72px */
  line-height: 1.06;
  letter-spacing: -0.025em;
  color: #0B234B;
  margin-top: 1.75rem;        /* 28px */
  margin-bottom: 0;
}

/* Dimmed second line */
%%SELECTOR%% .h1-dim {
  opacity: 0.72;
}
```

---

## Step 6 — Text (Body Paragraph)

Inside the **left column**, directly after the Heading, add a **Text** element.

**In the Breakdance panel:**

| Tab | Setting | Value |
|---|---|---|
| Content | Text | *Paste the full paragraph from your copy* |
| Typography | Font Family | `Plus Jakarta Sans` |
| Typography | Font Weight | `Light (300)` |
| Typography | Font Size | `17px` |
| Typography | Color | `#0B234B` at `60%` opacity |
| Spacing | Margin Top | `28px` |

**Custom CSS:**

```css
%%SELECTOR%% {
  font-family: 'Plus Jakarta Sans', system-ui, sans-serif;
  font-weight: 300;
  font-size: 1.0625rem;       /* 17px */
  line-height: 1.625;
  color: rgba(11, 35, 75, 0.60);
  max-width: 52ch;
  margin-top: 1.75rem;        /* 28px */
  margin-bottom: 0;
}
```

---

## Step 7 — Button (CTA)

Inside the **left column**, directly after the Text, add a **Button** element.

**In the Breakdance panel:**

| Tab | Setting | Value |
|---|---|---|
| Content | Label | `Unlock the Treasure Within` |
| Content | Link | `#pathways` (or your target URL) |
| Spacing | Margin Top | `40px` |

**Custom CSS:**

```css
%%SELECTOR%% {
  display: inline-flex;
  align-items: center;
  gap: 0.7rem;
  background-color: #BF8B19;
  color: #ffffff;
  font-family: 'Plus Jakarta Sans', system-ui, sans-serif;
  font-weight: 300;
  font-size: 0.8125rem;       /* 13px */
  letter-spacing: 0.025em;
  padding: 0.9rem 1.6rem;
  border-radius: 9999px;
  text-decoration: none;
  border: none;
  cursor: pointer;
  margin-top: 2.5rem;         /* 40px */
  transition: background-color 0.45s cubic-bezier(0.32, 0.72, 0, 1),
              transform 0.3s cubic-bezier(0.32, 0.72, 0, 1);
}

%%SELECTOR%%:hover {
  background-color: #a57816;
  transform: translateY(-1px);
}

%%SELECTOR%%:active {
  transform: scale(0.975);
}
```

---

## Step 8 — Div (Outer Bezel Frame)

Inside the **right column**, add a **Div** element. This is the outer decorative border frame around the hero image.

**In the Breakdance panel:**

| Tab | Setting | Value |
|---|---|---|
| Layout | Display | `Block` |

**Custom CSS:**

```css
%%SELECTOR%% {
  background-color: rgba(11, 35, 75, 0.04);
  border: 1px solid rgba(11, 35, 75, 0.09);
  padding: 7px;
  border-radius: 32px;
  position: relative;        /* needed for accent thumbnail in Step 11 */
}
```

---

## Step 9 — Div (Inner Bezel Core)

Inside the **Outer Bezel Div** (Step 8), add another **Div** element. This clips the image to the rounded shape.

**Custom CSS:**

```css
%%SELECTOR%% {
  border-radius: 25px;        /* 32px outer minus 7px padding */
  overflow: hidden;
}
```

---

## Step 10 — Image (Main Hero Image)

Inside the **Inner Bezel Core Div** (Step 9), add an **Image** element.

**In the Breakdance panel:**

| Tab | Setting | Value |
|---|---|---|
| Content | Image | Upload **Treasure Chest in the Sand** |
| Content | Alt Text | `A treasure chest resting in the sand — representing the riches God has placed inside every believer` |

**Custom CSS:**

```css
%%SELECTOR%% {
  width: 100%;
  display: block;
  object-fit: cover;
  object-position: center;
  aspect-ratio: 3 / 4;
}
```

---

## Step 11 — Div (Accent Thumbnail Wrapper)

Inside the **right column**, after the Outer Bezel Div (Step 8), add a **Div** element. This is the small overlapping image in the bottom-left corner of the hero image.

> This element is **hidden on mobile** and only appears on desktop (768px and above).

**Custom CSS:**

```css
%%SELECTOR%% {
  display: none;              /* hidden on mobile */
  position: absolute;
  bottom: -20px;
  left: -20px;
  width: 96px;
  height: 96px;
  background-color: rgba(11, 35, 75, 0.04);
  border: 1px solid rgba(11, 35, 75, 0.09);
  padding: 7px;
  border-radius: 32px;
  z-index: 2;
}

/* Show on desktop only */
@media (min-width: 768px) {
  %%SELECTOR%% {
    display: block;
  }
}
```

> **Important:** For this to position correctly, the **right column** also needs `position: relative`. Apply this to the right column's Custom CSS field:
>
> ```css
> %%SELECTOR%% {
>   position: relative;
> }
> ```

---

## Step 12 — Div (Accent Bezel Core)

Inside the **Accent Thumbnail Div** (Step 11), add a **Div** element. This clips the small image.

**Custom CSS:**

```css
%%SELECTOR%% {
  border-radius: 25px;
  overflow: hidden;
  height: 100%;
}
```

---

## Step 13 — Image (Accent Thumbnail)

Inside the **Accent Bezel Core Div** (Step 12), add an **Image** element.

**In the Breakdance panel:**

| Tab | Setting | Value |
|---|---|---|
| Content | Image | Upload **Clay Pots by Wall** |
| Content | Alt Text | Leave blank (decorative image) |

**Custom CSS:**

```css
%%SELECTOR%% {
  width: 100%;
  height: 100%;
  object-fit: cover;
  display: block;
}
```

---

## Entrance Animations (Optional)

Breakdance has a built-in animation system. Apply these settings to each element individually using the **Animation** tab in the Breakdance panel — no custom CSS needed for this.

| Element | Animation Type | Duration | Delay |
|---|---|---|---|
| Eyebrow Div (Step 3) | Fade Up | `0.85s` | `0ms` |
| Heading (Step 5) | Fade Up | `0.85s` | `100ms` |
| Body Text (Step 6) | Fade Up | `0.85s` | `200ms` |
| Button (Step 7) | Fade Up | `0.85s` | `300ms` |
| Outer Bezel Div (Step 8) | Fade Up | `0.85s` | `150ms` |
| Accent Thumbnail (Step 11) | Fade Up | `0.85s` | `400ms` |

---

## Quick Reference — All CSS in One Place

If you prefer to paste all hero CSS into a single location (e.g. **Global Styles → Custom CSS**), use this consolidated block. Assign the class names shown to each element using Breakdance's **CSS Classes** field.

```css
/* ── Section ───────────────────────────── */
.hero-section {
  position: relative;
  min-height: 100dvh;
  overflow: hidden;
  display: flex;
  align-items: center;
  background-color: #EDECE9;
}

.hero-section::before {
  content: '';
  position: absolute;
  top: 0; right: 0; bottom: 0; left: 0;
  background-image: url('PASTE_YOUR_TEXTURE_IMAGE_URL_HERE');
  background-size: cover;
  background-position: center;
  opacity: 0.05;
  pointer-events: none;
  z-index: 0;
}

/* ── Columns Grid ──────────────────────── */
.hero-columns {
  position: relative;
  z-index: 1;
  width: 100%;
  max-width: 1280px;
  margin: 0 auto;
  padding: 144px 24px 96px;
  box-sizing: border-box;
}

@media (min-width: 768px) {
  .hero-columns {
    padding: 160px 24px 112px;
    gap: 64px;
  }
}

@media (max-width: 767px) {
  .hero-columns {
    grid-template-columns: 1fr !important;
    gap: 40px;
  }
}

/* ── Eyebrow Tag ───────────────────────── */
.hero-eyebrow {
  display: inline-flex;
  align-items: center;
  font-family: 'Plus Jakarta Sans', system-ui, sans-serif;
  font-weight: 300;
  font-size: 0.625rem;
  text-transform: uppercase;
  letter-spacing: 0.2em;
  padding: 0.35rem 0.9rem;
  border-radius: 9999px;
  border: 1px solid rgba(11, 35, 75, 0.14);
  color: rgba(11, 35, 75, 0.75);
  background-color: rgba(11, 35, 75, 0.05);
}

.hero-eyebrow p {
  font-family: 'Plus Jakarta Sans', system-ui, sans-serif;
  font-weight: 300;
  font-size: 0.625rem;
  text-transform: uppercase;
  letter-spacing: 0.2em;
  color: rgba(11, 35, 75, 0.75);
  margin: 0;
  padding: 0;
  line-height: 1;
}

/* ── H1 Heading ────────────────────────── */
.hero-h1 {
  font-family: 'Oranienbaum', Georgia, serif;
  font-weight: 400;
  font-size: clamp(2.75rem, 6vw, 4.5rem);
  line-height: 1.06;
  letter-spacing: -0.025em;
  color: #0B234B;
  margin-top: 1.75rem;
  margin-bottom: 0;
}

.hero-h1 .h1-dim {
  opacity: 0.72;
}

/* ── Body Paragraph ────────────────────── */
.hero-body {
  font-family: 'Plus Jakarta Sans', system-ui, sans-serif;
  font-weight: 300;
  font-size: 1.0625rem;
  line-height: 1.625;
  color: rgba(11, 35, 75, 0.60);
  max-width: 52ch;
  margin-top: 1.75rem;
  margin-bottom: 0;
}

/* ── CTA Button ────────────────────────── */
.hero-btn {
  display: inline-flex;
  align-items: center;
  gap: 0.7rem;
  background-color: #BF8B19;
  color: #ffffff;
  font-family: 'Plus Jakarta Sans', system-ui, sans-serif;
  font-weight: 300;
  font-size: 0.8125rem;
  letter-spacing: 0.025em;
  padding: 0.9rem 1.6rem;
  border-radius: 9999px;
  text-decoration: none;
  border: none;
  cursor: pointer;
  margin-top: 2.5rem;
  transition: background-color 0.45s cubic-bezier(0.32, 0.72, 0, 1),
              transform 0.3s cubic-bezier(0.32, 0.72, 0, 1);
}

.hero-btn:hover {
  background-color: #a57816;
  transform: translateY(-1px);
}

.hero-btn:active {
  transform: scale(0.975);
}

/* ── Image Bezel (outer) ───────────────── */
.hero-bezel {
  background-color: rgba(11, 35, 75, 0.04);
  border: 1px solid rgba(11, 35, 75, 0.09);
  padding: 7px;
  border-radius: 32px;
  position: relative;
}

/* ── Image Bezel Core (inner) ──────────── */
.hero-bezel-core {
  border-radius: 25px;
  overflow: hidden;
}

/* ── Main Hero Image ───────────────────── */
.hero-img {
  width: 100%;
  display: block;
  object-fit: cover;
  object-position: center;
  aspect-ratio: 3 / 4;
}

/* ── Right Column ──────────────────────── */
.hero-img-col {
  position: relative;
}

/* ── Accent Thumbnail ──────────────────── */
.hero-accent {
  display: none;
  position: absolute;
  bottom: -20px;
  left: -20px;
  width: 96px;
  height: 96px;
  background-color: rgba(11, 35, 75, 0.04);
  border: 1px solid rgba(11, 35, 75, 0.09);
  padding: 7px;
  border-radius: 32px;
  z-index: 2;
}

@media (min-width: 768px) {
  .hero-accent {
    display: block;
  }
}

.hero-accent-core {
  border-radius: 25px;
  overflow: hidden;
  height: 100%;
}

.hero-accent-core img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  display: block;
}
```

> To use this block, add the corresponding class name from the left column of the table below to each element's **CSS Classes** field in Breakdance:

| Step | Element | Class to assign |
|---|---|---|
| 1 | Section | `hero-section` |
| 2 | Columns | `hero-columns` |
| 3 | Eyebrow Div | `hero-eyebrow` |
| 5 | Heading | `hero-h1` |
| 6 | Body Text | `hero-body` |
| 7 | Button | `hero-btn` |
| 8 | Outer Bezel Div | `hero-bezel` |
| 9 | Inner Bezel Div | `hero-bezel-core` |
| 10 | Main Image | `hero-img` |
| Right Column | Column | `hero-img-col` |
| 11 | Accent Thumb Div | `hero-accent` |
| 12 | Accent Core Div | `hero-accent-core` |

---

---

# Section 02 — Trust Bar (Marquee Slider)
*Kingdom Para Para · Free elements only · No Pro required*

---

## What This Section Does

A full-width band that sits immediately below the Hero, separated by a subtle top and bottom border. Three italic trust statements scroll continuously from right to left in a seamless loop, separated by gold diamond dividers. Hovering pauses the animation. The section has a photographic texture layered behind a semi-transparent parchment background, giving it depth without competing with the text.

---

## Element Structure Overview

```
1. Div  ←  outer wrapper (border top/bottom, overflow hidden)
├── 2. Div  ←  texture layer (absolute, Rocks & River image)
└── 3. Code Block  ←  marquee strip (parchment bg + scrolling text)
```

> **Why a Code Block?** Breakdance's free tier has no native ticker or marquee element. A Code Block lets you output the exact HTML structure and inline styles the animation needs without any third-party plugins.

---

## Global CSS — Add This First

Before building the elements, add the marquee animation to **Breakdance → Global Styles → Custom CSS**. This only needs to be done once for the whole site.

```css
/* ── Trust Bar Marquee ─────────────────── */
@keyframes marquee {
  from { transform: translateX(0); }
  to   { transform: translateX(-50%); }
}

.marquee-inner {
  display: flex;
  align-items: center;
  width: max-content;
  animation: marquee 40s linear infinite;
}

.marquee-inner:hover {
  animation-play-state: paused;
}
```

---

## Step 1 — Div (Outer Wrapper)

Add a **Div** element directly after your Hero Section. This is the outermost container — it handles the top/bottom border and clips the scrolling content.

**In the Breakdance panel:**

| Tab | Setting | Value |
|---|---|---|
| Layout | Display | `Block` |
| Layout | Overflow | `Hidden` |

**Custom CSS:**

```css
%%SELECTOR%% {
  position: relative;
  overflow: hidden;
  border-top: 1px solid rgba(11, 35, 75, 0.10);
  border-bottom: 1px solid rgba(11, 35, 75, 0.10);
}
```

---

## Step 2 — Div (Texture Layer)

Inside the outer wrapper, add a **Div** element. This is the photographic texture that sits behind the scrolling text at very low opacity.

**In the Breakdance panel:**

| Tab | Setting | Value |
|---|---|---|
| Content | Image | Upload **Rocks & River** |
| Background | Image Size | Cover |
| Background | Image Position | Center |

**Custom CSS:**

```css
%%SELECTOR%% {
  position: absolute;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  background-image: url('PASTE_YOUR_ROCKS_AND_RIVER_IMAGE_URL_HERE');
  background-size: cover;
  background-position: center;
  opacity: 0.055;
  pointer-events: none;
}
```

> Replace `PASTE_YOUR_ROCKS_AND_RIVER_IMAGE_URL_HERE` with the WordPress media URL for **Rocks & River** after uploading it.

---

## Step 3 — Code Block (Marquee Strip)

Inside the outer wrapper (sibling of the texture Div, **after** it), add a **Code Block** element. Switch the Code Block to **HTML** mode and paste the following exactly.

```html
<div style="position:relative;overflow:hidden;background-color:rgba(237,236,233,0.85);padding-top:1.25rem;padding-bottom:1.25rem;">
  <div class="marquee-inner" aria-label="Trust statements">

    <!-- ── Set 1 ───────────────────────────────── -->
    <span style="white-space:nowrap;padding-left:3rem;padding-right:3rem;color:rgba(11,35,75,0.65);font-family:'Newsreader',serif;font-weight:300;font-style:italic;font-size:0.9375rem;">
      For the one who loves God and still feels stuck.
    </span>
    <span style="color:#BF8B19;padding-left:0.25rem;padding-right:0.25rem;font-size:0.75rem;" aria-hidden="true">◆</span>

    <span style="white-space:nowrap;padding-left:3rem;padding-right:3rem;color:rgba(11,35,75,0.65);font-family:'Newsreader',serif;font-weight:300;font-style:italic;font-size:0.9375rem;">
      For the believer whose faith and everyday life do not yet feel connected.
    </span>
    <span style="color:#BF8B19;padding-left:0.25rem;padding-right:0.25rem;font-size:0.75rem;" aria-hidden="true">◆</span>

    <span style="white-space:nowrap;padding-left:3rem;padding-right:3rem;color:rgba(11,35,75,0.65);font-family:'Newsreader',serif;font-weight:300;font-style:italic;font-size:0.9375rem;">
      For the one who keeps starting over and is ready for something to finally take root.
    </span>
    <span style="color:#BF8B19;padding-left:0.25rem;padding-right:0.25rem;font-size:0.75rem;" aria-hidden="true">◆</span>

    <!-- ── Set 2 (duplicate — required for seamless loop) ── -->
    <span style="white-space:nowrap;padding-left:3rem;padding-right:3rem;color:rgba(11,35,75,0.65);font-family:'Newsreader',serif;font-weight:300;font-style:italic;font-size:0.9375rem;">
      For the one who loves God and still feels stuck.
    </span>
    <span style="color:#BF8B19;padding-left:0.25rem;padding-right:0.25rem;font-size:0.75rem;" aria-hidden="true">◆</span>

    <span style="white-space:nowrap;padding-left:3rem;padding-right:3rem;color:rgba(11,35,75,0.65);font-family:'Newsreader',serif;font-weight:300;font-style:italic;font-size:0.9375rem;">
      For the believer whose faith and everyday life do not yet feel connected.
    </span>
    <span style="color:#BF8B19;padding-left:0.25rem;padding-right:0.25rem;font-size:0.75rem;" aria-hidden="true">◆</span>

    <span style="white-space:nowrap;padding-left:3rem;padding-right:3rem;color:rgba(11,35,75,0.65);font-family:'Newsreader',serif;font-weight:300;font-style:italic;font-size:0.9375rem;">
      For the one who keeps starting over and is ready for something to finally take root.
    </span>
    <span style="color:#BF8B19;padding-left:0.25rem;padding-right:0.25rem;font-size:0.75rem;" aria-hidden="true">◆</span>

  </div>
</div>
```

> **Why duplicate the content?** The marquee works by translating the strip exactly −50% of its total width, then resetting to 0 and looping. With two identical sets of statements, the reset is invisible — the end of set 2 looks exactly like the start of set 1.

---

## Typography Details

| Property | Value |
|---|---|
| Font family | Newsreader |
| Font weight | Light (300) |
| Font style | Italic |
| Font size | `0.9375rem` — **15px** |
| Text colour | `rgba(11, 35, 75, 0.65)` — Navy at 65% opacity |
| Separator | `◆` gold diamond at `0.75rem` / `12px` |
| Separator colour | `#BF8B19` — Yellow Gold |

---

## Animation Details

| Property | Value |
|---|---|
| Direction | Right → Left |
| Duration | `40s` |
| Timing | Linear (constant speed, no easing) |
| Loop | Infinite |
| Hover behaviour | Pauses on mouse-over |
| Technique | CSS `@keyframes` on the inner flex container |

---

## Section Visual Details

| Property | Value |
|---|---|
| Border | `1px solid rgba(11, 35, 75, 0.10)` — top and bottom |
| Background | `rgba(237, 236, 233, 0.85)` — Stone at 85% opacity |
| Texture | Rocks & River image at `5.5%` opacity (absolute, fills wrapper) |
| Padding | `20px` top and bottom |
| Overflow | Hidden (cuts off text as it exits either edge) |

---

## Quick Reference — Global CSS Block

Add this once to **Global Styles → Custom CSS** (not per-element):

```css
/* ── Section 02 — Trust Bar Marquee ──── */
@keyframes marquee {
  from { transform: translateX(0); }
  to   { transform: translateX(-50%); }
}

.marquee-inner {
  display: flex;
  align-items: center;
  width: max-content;
  animation: marquee 40s linear infinite;
}

.marquee-inner:hover {
  animation-play-state: paused;
}
```

And add this once to **Global Styles → Custom CSS** for the outer wrapper (or use a CSS class via Breakdance's CSS Classes field):

```css
/* ── Trust Bar Wrapper ──────────────── */
.trust-bar {
  position: relative;
  overflow: hidden;
  border-top: 1px solid rgba(11, 35, 75, 0.10);
  border-bottom: 1px solid rgba(11, 35, 75, 0.10);
}

.trust-bar-texture {
  position: absolute;
  inset: 0;
  background-image: url('PASTE_YOUR_ROCKS_AND_RIVER_IMAGE_URL_HERE');
  background-size: cover;
  background-position: center;
  opacity: 0.055;
  pointer-events: none;
}
```

| Step | Element | Class to assign |
|---|---|---|
| 1 | Outer Wrapper Div | `trust-bar` |
| 2 | Texture Div | `trust-bar-texture` |
| 3 | Code Block | *(no class needed — markup is self-contained)* |
