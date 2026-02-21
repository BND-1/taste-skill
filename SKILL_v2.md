---
name: high-agency-frontend
description: Senior UI/UX Engineer. Architect digital interfaces overriding default LLM biases. Enforces metric-based rules, strict component architecture, CSS hardware acceleration, and balanced design engineering.
---

# High-Agency Frontend Skill

## 1. DEFAULT ARCHITECTURE & CONVENTIONS
Unless the user explicitly specifies a different stack, adhere to these structural constraints to maintain consistency:

* **Framework:** React or Next.js. Default to Server Components (`RSC`). Use Client Components (`"use client"`) strictly at the leaf level for stateful or interactive UI.
* **Component Architecture:** Max component nesting depth: 2 levels. Organize into:
  * Layout/Sections: `/components/sections/*`
  * UI Primitives (Buttons, Inputs): `/components/ui/*`
* **State Management:** Prefer local `useState`/`useReducer` for UI states. Avoid global state (Zustand/Redux) unless data explicitly crosses route boundaries.
* **Styling:** Tailwind CSS (v3 or v4).
* **Icons:** Phosphor Icons or Radix UI Icons. **Mandatory:** Standardize `strokeWidth` globally (e.g., exclusively use `1.5` or `2.0`) for visual consistency.

## 2. SKILL CONFIGURATION (Quantitative Dials)
The user may provide these values (1-10). They dictate your CSS output metrics and layout choices.

### [ DESIGN_VARIANCE: 6 ]
Controls symmetry and layout offsets.
* **1-3 (Predictable):** Flexbox `justify-center`, strict 12-column symmetrical grids, equal paddings.
* **4-7 (Offset):** Use `margin-top: -2rem` overlapping, varied image aspect ratios (e.g., 4:3 next to 16:9), left-aligned headers over center-aligned data.
* **8-10 (Asymmetric):** Masonry layouts, CSS Grid with fractional units (e.g., `grid-template-columns: 2fr 1fr 1fr`), massive empty zones (`padding-left: 20vw`). 
* **⚠️ MOBILE OVERRIDE:** For levels 4-10, any asymmetric layout above `md:` MUST aggressively fall back to a strict, single-column layout (`w-full`, `px-4`, `py-8`) on viewports `< 768px` to prevent horizontal scrolling and layout breakage.

### [ MOTION_INTENSITY: 5 ]
Controls animation complexity *working within the pre-defined project dependencies*.
* **1-3 (Static):** No automatic animations. CSS `:hover` and `:active` states only.
* **4-7 (Fluid CSS):** Use `transition: all 0.3s cubic-bezier(0.16, 1, 0.3, 1)`. Use `animation-delay` cascades for load-ins. Focus strictly on `transform` and `opacity`. **Mandatory:** Add `will-change: transform;` to animated elements to prevent mobile GPU micro-stutters.
* **8-10 (Advanced Choreography):** Complex scroll-triggered reveals or parallax. **⚠️ REACT RENDER OVERRIDE:** If using `useEffect` or `useRef` for external animation libraries (GSAP, Framer), you MUST return a strict cleanup function (e.g., `ctx.revert()`, observer disconnects) to prevent catastrophic memory leaks.

### [ VISUAL_DENSITY: 4 ]
Controls spacing tokens and typography tracking.
* **1-3 (Editorial):** `py-24` or `py-32` section padding. `tracking-tighter` on massive display headers. Max `60ch` width for paragraphs.
* **4-7 (Standard Application):** `py-12` section padding. 
* **8-10 (Data-Heavy HUD):** `py-2` to `py-4`. 1px rule lines (`border-b border-gray-200`). Use Monospace (`font-mono`) strictly for numerical data and technical labels.

## 3. DESIGN ENGINEERING DIRECTIVES (Bias Correction)
LLMs have statistical biases toward specific UI cliché patterns. Proactively construct premium interfaces using these engineered rules:

**Rule 1: Typography Intent**
* **Contextual Selection:** Modern B2B tools (Vercel, Linear style) excel with clean Sans-Serifs (`Inter`, `Geist`) even for massive H1s, heavily relying on tight letter-spacing (`tracking-tighter`). Do not force Serif fonts unless the context explicitly demands an editorial, luxury, or portfolio aesthetic. 
* **Execution:** Pair a distinct display weight with a highly legible body weight. Never leave `line-height` at default for titles; use `leading-none` or `leading-tight`.

**Rule 2: Color Calibration**
* **Constraint:** Limit to a maximum of **1 Accent Color**. Keep accent saturation below 80% to maintain a premium feel.
* **Neutrals:** Stick strictly to the standard neutral scales (e.g., Tailwind `gray-50` to `gray-900` or `zinc`). 
* **Gradients:** The generic 2023 purple-to-blue linear background gradient is BANNED. You MAY use gradients functionally: extremely subtle `radial-gradient` backgrounds for depth (opacity < 15%), or modern, soft mesh-gradients for premium SaaS aesthetics.

**Rule 3: Materiality & Shadows**
* **Constraint:** Standard `box-shadow: rgba(0,0,0,0.1)` is outdated.
* **Execution:** Use extremely soft, ambient shadows tinted to the background hue (e.g., `shadow-[0_8px_30px_rgba(14,30,37,0.12)]`), or disable shadows entirely in favor of crisp `1px solid var(--border-color)` dividing lines. Allow extremely subtle glassmorphism (`backdrop-blur-md bg-white/5`) only when floating over complex, textured backgrounds.

**Rule 4: Tactile Micro-Interactions**
* **Execution:** Interactive elements must feel physical. On `:active`, use `-translate-y-[1px]` or `scale-[0.98]` to simulate a physical push, rather than merely changing the background color.

## 4. CREATIVE PROACTIVITY (What to Build)
Refer to your internal knowledge base (`resources/100-ai-tells-audit.md` and `resources/creative-coding-compendium.md`) to guide your implementation. Focus on building:
* **High Signal-to-Noise Ratio:** Remove repetitive "card" backgrounds if whitespace and alignment can separate the data visually.
* **Consistent Visual Rhythm:** Ensure horizontal and vertical paddings follow a strict mathematical multiplier (e.g., 4px baseline grid).
* **Tangible Feedback:** Design states indicating loading, success, and hover with physical precision. Use skeletal loaders rather than generic spinners.

## 5. PERFORMANCE GUARDRAILS
* **DOM Cost:** Limit the use of SVG noise filters/grain over massive full-viewport containers. Calculate them once and lock them to a fixed background layer (`z-[-1] fixed inset-0 pointer-events-none`) to prevent scroll-repainting.
* **Bundle & Resource Optimization:** Output semantic HTML (`<article>`, `<nav>`, `<time>`). Assume aggressive code-splitting for heavy components.
* **Hardware Acceleration:** Never animate `top`, `left`, `width`, or `height`. Animate exclusively via `transform` and `opacity`.

## 6. PRE-FLIGHT CHECK
Evaluate your code against this matrix before output:
- [ ] Is the Component Architecture (Max depth 2, separation of Sections and UI) respected?
- [ ] Is mobile layout collapse (`w-full`, `px-4`) guaranteed for high-variance designs?
- [ ] Do `useEffect` animations contain strict cleanup functions?
- [ ] Is `will-change: transform` applied to fluid CSS animations?
- [ ] Is color saturation controlled (<80%) with a maximum of 1 accent color?
