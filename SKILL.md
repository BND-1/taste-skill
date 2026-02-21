---
name: anti-slop-frontend
description: Creative Technologist & Senior Frontend Engineer skill. Architect digital artifacts that transcend utility — interfaces that feel like physical objects, avant-garde magazines, or precision instruments. Enforces strict anti-patterns, advanced kinetic techniques, and contextual aesthetic modes to eradicate "AI Slop" from every output.
---

# Anti-Slop Frontend Skill

## Mission
Build interfaces that feel like **physical objects**, avant-garde magazines, or precision instruments.  
**PRIME DIRECTIVE**: Eliminate all generic patterns. If the output resembles a standard template, a Dribbble clone, or a default component library, it is a **failure**.

---

## 1. THE ANTI-PATTERNS (STRICTLY FORBIDDEN)

Before writing a single line of CSS, internalize these forbidden patterns.

### Visual Syntax Errors

| ❌ Forbidden | ✅ Alternative |
|---|---|
| Purple-to-blue tech gradient | Muted editorial tones, grain overlays, or hard geometric color blocks |
| Neon / outer glow box-shadows | Hard-edged retro shadows, colored shadows matching bg hue, or no shadow at all |
| Glassmorphism everywhere | Solid opacity layers, dithering patterns, or tactile texture instead of blur |
| Pure black alpha shadows | Colored shadows (e.g., deep navy on blue bg) or flat neo-brutalist borders |
| Perfect center alignment | Asymmetric layouts; indent unexpectedly; left-anchor with intentional offset |

### Component Clichés

| ❌ Forbidden | ✅ Alternative |
|---|---|
| 3-column rounded bento grid | Broken grids, masonry layouts, or overlapping sections |
| Rocket / shield / lock icons | Abstract geometry, technical crosshairs, or raw typographic marks |
| Pill badges (fully rounded) | Square flags, technical labels, 1px bracket borders `[ label ]` |
| White card + gray border + drop shadow | Negative margins, spacing-defined sections, invisible boundaries |

---

## 2. THE CREATIVE ENGINE (ADVANCED TECHNIQUES)

### Kinetic Typography — Make Text Liquid

- **Velocity Skew**: Text reacts to scroll speed using `transform: skewX()` tied to scroll delta.
- **Infinite Marquee**: Looping bands of oversized type create momentum and rhythm.
  ```css
  /* Marquee base pattern */
  @keyframes marquee { from { transform: translateX(0) } to { transform: translateX(-50%) } }
  .marquee-inner { animation: marquee 12s linear infinite; white-space: nowrap; }
  ```
- **Mix-Blend-Mode Text**: Text color flips as it passes over images.
  ```css
  .kinetic-heading { mix-blend-mode: difference; color: white; }
  ```
- **Masked Typography**: Text acts as a window revealing video/gradient underneath via `background-clip: text`.

### Immersive Scrolling — Control Time

- **Parallax Stacking**: Sections don't scroll past — they **stack like cards** using `position: sticky; top: 0`.
- **Horizontal-Vertical Hybrid**: Vertical scroll triggers horizontal gallery movement.
  - Use `IntersectionObserver` to switch scroll axis on a pinned container.
- **Sticky Pinning**: Lock a visual element (image / 3D canvas) while narrative text scrolls over it.
  ```css
  .pinned-visual { position: sticky; top: 10vh; height: 80vh; }
  .scroll-narrative { position: relative; z-index: 10; }
  ```

### Micro-Interactions — The Tactile Feel

- **Magnetic Elements**: Buttons physically pull toward the cursor.
  ```js
  el.addEventListener('mousemove', e => {
    const { left, top, width, height } = el.getBoundingClientRect();
    const x = (e.clientX - left - width / 2) * 0.3;
    const y = (e.clientY - top - height / 2) * 0.3;
    el.style.transform = `translate(${x}px, ${y}px)`;
  });
  el.addEventListener('mouseleave', () => el.style.transform = '');
  ```
- **Cursor Displacement**: Cursor acts as a spotlight, lens, or distortion field.
  ```css
  .cursor-glow { 
    position: fixed; pointer-events: none; 
    width: 300px; height: 300px;
    background: radial-gradient(circle, rgba(255,255,255,0.05) 0%, transparent 70%);
    transform: translate(-50%, -50%);
    mix-blend-mode: screen;
  }
  ```
- **Dithering & Grain**: Replace smooth gradients with CSS noise for "Lo-Fi High-Tech" texture.
  ```css
  /* SVG noise filter approach */
  .grain-overlay::after {
    content: '';
    position: absolute; inset: 0;
    background-image: url("data:image/svg+xml,..."); /* base64 noise SVG */
    opacity: 0.04;
    pointer-events: none;
  }
  ```

---

## 3. CONTEXTUAL MODES — THE VIBE CHECK

**Select EXACTLY ONE mode per project. Do not mix randomly.**

### MODE A — THE "EDITORIAL"
*For: Content sites, portfolios, blogs, magazines*

> The web page is a printed fashion magazine that has come alive.

- **Typography**: Massive serif headers (Playfair Display, Cormorant Garamond). Text overlaps images.
- **Layout**: Asymmetric. Text floats over imagery. Whitespace is aggressive.
- **Palette**: Off-white `#F5F0E8` + Deep ink black `#0D0B08` + One clash color (Acid Green `#BFFF00` or International Orange `#FF4500`)
- **Key Tech**: Smooth parallax, text reveal animations (clip-path), mix-blend-mode overlaps
- **Font Stack**: `'Cormorant Garamond', 'Playfair Display', Georgia, serif`

### MODE B — THE "PRECISION INSTRUMENT"
*For: Dashboards, tools, data products, developer utilities*

> The interface is a physical tool — a Braun calculator or a Teenage Engineering synthesizer.

- **Typography**: Monospace mandatory for data. Small uppercase labels. Stark scale contrast.
- **Layout**: 1px rule lines dividing sections. Crosshairs. Coordinate numbers as decorative elements.
- **Palette**: Muted greys, dust, clay, sage. High-contrast strokes. Film look — no pure black.
  - Background: `#F4F1EC` | Stroke: `#2A2A2A` | Accent: `#D4603A` (rust)
- **Key Tech**: Snap transitions, slot-machine number animations, dense info without clutter
- **Font Stack**: `'JetBrains Mono', 'IBM Plex Mono', monospace`

### MODE C — THE "INSTALLATION"
*For: Landing pages, experiences, portfolios, brand statements*

> The browser is a canvas for art. Physics governs the layout.

- **Typography**: Fluid sizing (`clamp()`). Brutalist grotesque or mono. Abstract over literal.
- **Layout**: Full-viewport. Organic blobs, brutalist raw HTML, or fluid simulations.
- **Palette**: Monochrome or dark mode with subtle noise. One controlled color surprise.
  - Background: `#080808` | Foreground: `#F0F0F0` | Noise opacity: 3-5%
- **Key Tech**: WebGL-style distortion (CSS filters + SVG), cursor trails, fluid typography
- **Font Stack**: `'Space Grotesk', 'DM Mono', sans-serif`

---

## 4. VISUAL SYSTEM — SOPHISTICATED CHAOS

### Typography Scale
```css
/* The Extremes — use both ends, nothing in between */
.headline    { font-size: clamp(4rem, 12vw, 10rem); line-height: 0.9; letter-spacing: -0.03em; }
.subheadline { font-size: clamp(1.5rem, 3vw, 2.5rem); }
.label       { font-size: 0.65rem; text-transform: uppercase; letter-spacing: 0.15em; }
.body        { font-size: 1rem; line-height: 1.7; max-width: 60ch; }
```

### Layout Principles
- **Neo-Brutalism**: Raw borders (`border: 1px solid`), visible grid lines (`outline`), unstyled HTML purposefully exposed.
- **Overlap**: Titles sit on top of photos. Buttons straddle borders. Use `margin-top: -2rem` aggressively.
- **Whitespace**: 40% of viewport can be empty to frame a single element. Emptiness is a design choice.
- **Grid**: Avoid 12-column. Use `grid-template-columns: 3fr 1fr` or asymmetric definitions.

### Motion System
```css
/* Spring physics — no linear animations */
* { transition-timing-function: cubic-bezier(0.34, 1.56, 0.64, 1); } /* spring overshoot */

/* Stagger cascade — reveal line by line */
.reveal-line { 
  opacity: 0; transform: translateY(1.2em);
  animation: reveal 0.6s cubic-bezier(0.34, 1.56, 0.64, 1) forwards;
}
@keyframes reveal { to { opacity: 1; transform: translateY(0); } }
```

---

## 5. EXECUTION SCENARIOS

### Scenario: Login Form
- ❌ **AI Flop**: Centered card, blue button, shadow.
- ✅ **Anti-Slop Solution**: Split screen. Left = shifting noise curtain. Right = Technical UI — inputs defined only by 1px bottom borders. Submit = magnetic text label that follows cursor. Strictly monospace.

### Scenario: Portfolio
- ❌ **AI Flop**: Hero image + 3 text columns.
- ✅ **Anti-Slop Solution**: User's name as an infinite vertical marquee loop. Projects as parallax-stacked images that reveal on scroll. Cursor uses `mix-blend-mode: difference`, inverting colors as it moves.

### Scenario: Dashboard
- ❌ **AI Flop**: Sidebar, white cards, drop shadows.
- ✅ **Anti-Slop Solution**: Blueprint rule lines (1px grid). No shadows. Grainy off-white bg. Data updates trigger slot-machine number shuffle. Looks like a financial terminal.

---

## 6. QUALITY ASSURANCE CHECKLIST

Before outputting any code, verify:

- [ ] **Safe?** — Does the creativity break usability on mobile? If yes, simplify mobile while keeping desktop wild.
- [ ] **Not Boring?** — Is there a "Standard Card" or a Tailwind-blue button? If yes, kill it.
- [ ] **Not Slop?** — Does it look like a template? If yes, restart.
- [ ] **Is it Art?** — Does it feel like a designed object? If yes, ship it.

---

## 7. FORBIDDEN COMBINATIONS (QUICK REFERENCE)

```
purple → blue gradient       ❌
rounded pill badge            ❌
white card + gray border      ❌
centered hero with subtext    ❌
rocket/shield icon            ❌
glassmorphism as default      ❌
linear animation timing       ❌
12-column bento grid          ❌
pure black shadow             ❌
centered everything           ❌
```

---

## 8. RESOURCE REFERENCES

- **Fonts**: [Google Fonts — Cormorant Garamond](https://fonts.google.com/specimen/Cormorant+Garamond), [JetBrains Mono](https://fonts.google.com/specimen/JetBrains+Mono), [Space Grotesk](https://fonts.google.com/specimen/Space+Grotesk)
- **Inspiration (study, don't clone)**: Refinery29, Are.na, Cargo Collective, Virgil Abloh's work
- **CSS Tricks**: `mix-blend-mode`, `clip-path`, `scroll-timeline`, `@starting-style`
- **Examples**: See `examples/` directory in this skill for implementation patterns.
