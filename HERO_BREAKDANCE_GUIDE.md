# Kingdom Para Para — Breakdance Builder Guide
*Free elements only · No Pro required*

---

# Navigation Bar
*Built in Breakdance → Templates → Add Custom Template*

---

## How the Nav Works

The navbar is a **floating pill** fixed to the top of every page. Nav links come from a WordPress menu connected to Breakdance's native **Nav Menu** element, which handles desktop display and the mobile hamburger automatically. All styling is done via each element's own **Custom CSS** field using `%%SELECTOR%%` — no CSS classes required.

| Where | What goes there |
|---|---|
| **WordPress → Appearance → Menus** | Create the menu items |
| **Breakdance → Templates → Add Custom Template** | Build the nav elements |
| **Each element's Custom CSS field** | All styling via `%%SELECTOR%%` |

---

## Element Structure Overview

```
Custom Template
└── Section  ←  transparent, fixed, centered
    └── Div  ←  navy pill container
        ├── Image  ←  logo (linked to homepage)
        ├── Nav Menu  ←  desktop links + mobile hamburger (native)
        └── Button  ←  "Begin Here" CTA (hidden on mobile)
```

---

## Step 0A — Create Your WordPress Menu

The Nav Menu element in Breakdance pulls its links from a WordPress menu. Set this up first.

1. Go to **WordPress → Appearance → Menus**
2. Click **Create a new menu**
3. Name it `Main Nav`
4. Under **Menu items**, add four **Custom Links**:

| Label | URL |
|---|---|
| `About` | `#about` |
| `Pathways` | `#pathways` |
| `Devotional` | `#devotional` |
| `Storehouse` | `#storehouse` |

5. Click **Save Menu**

---

## Step 0B — Create the Custom Template

1. Go to **Breakdance → Templates**
2. Click **Add Template** → select **Add Custom Template**
3. Name it `Main Navigation`
4. Click **Edit with Breakdance** to open the canvas
5. In the top bar, find **Display Conditions** and set it to **Entire Site**

> Because the Section inside this template uses `position: fixed`, the nav floats above all page content regardless of where Breakdance injects the template markup. The display condition simply ensures it loads on every page.

---

## Step 1 — Section (Outer Wrapper)

Breakdance adds a Section automatically when you open the canvas. Select it and configure:

| Tab | Setting | Value |
|---|---|---|
| Background | Color | None / Transparent |
| Spacing | Padding | `20px` top · `16px` left & right · `0` bottom |

**Custom CSS** (paste into the element's Custom CSS field):

```css
%%SELECTOR%% {
  display: flex;
  justify-content: center;
  width: 100%;
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  z-index: 50;
}
```

> `position: fixed` is what makes the nav float above the page at all times.

---

## Step 2 — Div (Pill Container)

Inside the Section, add a **Div** element.

**Custom CSS:**

```css
%%SELECTOR%% {
  display: flex;
  align-items: center;
  gap: 20px;
  background-color: rgba(11, 35, 75, 0.90);
  backdrop-filter: blur(24px);
  -webkit-backdrop-filter: blur(24px);
  border-radius: 9999px;
  padding: 2px 12px 2px 16px;
  border: 1px solid rgba(255, 255, 255, 0.10);
  box-shadow: 0 8px 40px rgba(11, 35, 75, 0.30);
  width: 100%;
  max-width: 1280px;
  box-sizing: border-box;
}
```

---

## Step 3 — Image (Logo)

Inside the pill Div, add an **Image** element.

| Tab | Setting | Value |
|---|---|---|
| Content | Image | Upload **Kingdom Para Para Logo Transparent** |
| Content | Link URL | `/` |
| Content | Link Target | Same tab |
| Content | Alt Text | `Kingdom Para Para` |

**Custom CSS:**

```css
%%SELECTOR%% {
  height: 64px;
  width: auto;
  display: block;
  flex-shrink: 0;
}
```

---

## Step 4 — Nav Menu

Inside the pill Div, after the Image, add a **Nav Menu** element.

**In the Breakdance panel:**

| Tab | Setting | Value |
|---|---|---|
| Content | Menu | Select `Main Nav` |
| Layout | Mobile Breakpoint | `768px` |

**Custom CSS:**

```css
/* Fill the remaining space and push links to the right */
%%SELECTOR%% {
  flex: 1;
  display: flex;
  justify-content: flex-end;
  align-items: center;
}

/* Desktop link styling */
%%SELECTOR%% a {
  font-family: 'Plus Jakarta Sans', system-ui, sans-serif;
  font-weight: 300;
  font-size: 0.775rem;
  letter-spacing: 0.025em;
  color: rgba(255, 255, 255, 0.72);
  text-decoration: none;
  transition: color 0.3s ease;
}

%%SELECTOR%% a:hover {
  color: #ffffff;
}

/* Mobile menu panel */
%%SELECTOR%% .bde-nav-menu__mobile-menu {
  background-color: rgba(11, 35, 75, 0.97);
  padding: 40px 24px;
}

%%SELECTOR%% .bde-nav-menu__mobile-menu a {
  font-family: 'Oranienbaum', Georgia, serif;
  font-size: clamp(1.5rem, 6vw, 2.5rem);
  color: #ffffff;
}

%%SELECTOR%% .bde-nav-menu__mobile-menu a:hover {
  color: #BF8B19;
}
```

> **Important:** The class names for the mobile menu panel (e.g. `.bde-nav-menu__mobile-menu`) are Breakdance's internal names and may differ on your install. After building, right-click the mobile menu on your live page → **Inspect** to find the exact class names Breakdance generates, then update those selectors here to match.

---

## Step 5 — Button (CTA, desktop only)

Inside the pill Div, after the Nav Menu, add a **Button** element.

| Tab | Setting | Value |
|---|---|---|
| Content | Label | `Begin Here` |
| Content | Link | `#pathways` |

**Custom CSS:**

```css
%%SELECTOR%% {
  display: none;
  align-items: center;
  background-color: #BF8B19;
  color: #ffffff;
  font-family: 'Plus Jakarta Sans', system-ui, sans-serif;
  font-weight: 300;
  font-size: 0.75rem;
  letter-spacing: 0.05em;
  padding: 8px 20px;
  border-radius: 9999px;
  border: none;
  cursor: pointer;
  white-space: nowrap;
  text-decoration: none;
  flex-shrink: 0;
  transition: background-color 0.3s ease;
}

%%SELECTOR%%:hover {
  background-color: #a57816;
}

@media (min-width: 768px) {
  %%SELECTOR%% {
    display: inline-flex;
  }
}
```

---

## Nav Design Reference

| Property | Value |
|---|---|
| Nav style | Floating pill — centered, fixed |
| Background | `rgba(11, 35, 75, 0.90)` — Navy at 90% |
| Blur | `backdrop-filter: blur(24px)` |
| Border | `1px solid rgba(255, 255, 255, 0.10)` |
| Shadow | `0 8px 40px rgba(11, 35, 75, 0.30)` |
| Logo height | `64px` |
| Link font | Plus Jakarta Sans Light 300 / 12.4px |
| Link colour | White 72% → White 100% on hover |
| CTA | `#BF8B19` Yellow Gold → `#a57816` on hover |
| Mobile | Nav Menu native hamburger → styled panel |
| Mobile link font | Oranienbaum, fluid `1.5rem–2.5rem` |

---

---

# Hero Section — Breakdance Builder Step-by-Step Guide
*Free elements only · No Pro required*

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
└── 3. Rich Text  ←  marquee strip (parchment bg + scrolling text)
```

> **Why a Rich Text element?** Breakdance's Rich Text element has an HTML source view — click the **Source** button (looks like `<>`) in the toolbar to switch from the visual editor to raw HTML mode. This lets you paste the marquee markup directly. No Pro required.

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

## Step 3 — Rich Text (Marquee Strip)

Inside the outer wrapper (sibling of the texture Div, **after** it), add a **Rich Text** element.

When the element opens in the Breakdance panel, look for the **Source** button (`<>`) in the text editor toolbar and click it to switch to HTML mode. Delete any placeholder content Breakdance inserted, then paste the following exactly.

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
| 3 | Rich Text | *(no class needed — markup is self-contained)* |
