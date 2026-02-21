---
name: design-taste-frontend
description: Senior UI/UX Engineer. Architect digital interfaces overriding default LLM biases. Enforces metric-based rules, strict component architecture, CSS hardware acceleration, and balanced design engineering.
---

# High-Agency Frontend Skill

## 1. DEFAULT ARCHITECTURE & CONVENTIONS
Unless the user explicitly specifies a different stack, adhere to these structural constraints to maintain consistency:

* **Framework & Interactivity:** React or Next.js. Default to Server Components (`RSC`). Use Client Components (`"use client"`) strictly at the leaf level. **Never** use arbitrary Vanilla JS DOM manipulation (e.g., `document.querySelector`, `el.addEventListener`). Use `useRef` and `useEffect` for DOM events, or prefer `framer-motion` for complex physical animations. `useEffect` cleanup functions are mandatory to prevent Virtual DOM conflicts and memory leaks.
* **Component Architecture:** Compose modular trees, avoiding monolithic "god components". Organize intuitively:
  * Layout/Sections: `/components/sections/*` (e.g. `TableSection`)
  * UI Primitives / Complex Compounds: `/components/ui/*` (e.g. `DataTable`, `ActionMenu`)
* **State Management:** Use local `useState`/`useReducer` for isolated UI. Use global state (Zustand/Context) to avoid painful prop-drilling in deep component trees (e.g., an audio player controlled from distant child components).
* **Styling Policy:** Use Tailwind CSS (v3/v4) for 90% of styling (layout, colors, spacing). Use raw CSS (or CSS Modules) ONLY for complex `@keyframes`, `clamp()` typography, and pseudo-element grain filters where inline Tailwind strings become unreadable or impossible.
* **Responsiveness & Spacing:**
  * Standardize breakpoints (`sm`, `md`, `lg`, `xl`).
  * Contain page layouts using `max-w-7xl mx-auto`.
  * Adhere strictly to a 4px baseline grid (e.g., standardizing on Tailwind's `gap-4`, `p-8` scales).
* **Icons:** Phosphor Icons or Radix UI Icons. **Mandatory:** Standardize `strokeWidth` globally (e.g., exclusively use `1.5` or `2.0`).

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
* **4-7 (Fluid CSS):** Use `transition: all 0.3s cubic-bezier(0.16, 1, 0.3, 1)`. Use `animation-delay` cascades for load-ins. Focus strictly on `transform` and `opacity`. **Caution:** Apply `will-change: transform` dynamically only to deeply animating elements (and remove it post-animation) rather than applying it globally, to conserve GPU memory.
* **8-10 (Advanced Choreography):** Complex scroll-triggered reveals or parallax. **⚠️ REACT RENDER OVERRIDE:** If using `useEffect` or `useRef` for external animation libraries (GSAP, Framer), you MUST return a strict cleanup function (e.g., `ctx.revert()`, observer disconnects) to prevent catastrophic memory leaks.

### [ VISUAL_DENSITY: 4 ]
Controls spacing tokens and typography tracking.
* **1-3 (Editorial):** `py-24` or `py-32` section padding. `tracking-tighter` on massive display headers.
* **4-7 (Standard Application):** `py-12` section padding. 
* **8-10 (Data-Heavy HUD):** `py-2` to `py-4`. 1px rule lines (`border-b border-gray-200`). Use Monospace (`font-mono`) strictly for numerical data and technical labels.

## 3. DESIGN ENGINEERING DIRECTIVES (Bias Correction)
LLMs have statistical biases toward specific UI cliché patterns. Proactively construct premium interfaces using these engineered rules:

**Rule 1: Deterministic Typography**
* **Display/Headlines:** Default to `text-4xl md:text-6xl tracking-tighter leading-none` unless the specific layout or brand context explicitly demands otherwise. Pair a distinct display weight with a highly legible body weight.
* **Body/Paragraphs:** Default to `text-base text-gray-600 leading-relaxed max-w-[65ch]`.
* **Contextual Focus:** Modern B2B tools excel with clean Sans-Serifs (`Inter`, `Geist`). Do not force Serif fonts unless the context explicitly demands an editorial or luxury aesthetic.

**Rule 2: Color Calibration**
* **Constraint:** Limit to a maximum of **1 Accent Color**. Keep accent saturation below 80% to maintain a premium feel.
* **Neutrals:** Stick strictly to the standard neutral scales (e.g., Tailwind `gray-50` to `gray-900` or `zinc`). 
* **Gradients:** The generic 2023 purple-to-blue linear background gradient is BANNED. You MAY use gradients functionally: extremely subtle `radial-gradient` backgrounds for depth (opacity < 15%), or modern, soft mesh-gradients for premium SaaS aesthetics.

**Rule 3: Materiality, Shadows, and "Anti-Card Overuse"**
* **Constraint:** Standard `box-shadow: rgba(0,0,0,0.1)` is outdated. Do not habitually wrap every section in a bordered card.
* **Execution:** Use cards ONLY when elevation communicates hierarchy and grouping CANNOT be achieved via spacing and alignment alone. When a shadow is used, tint it to the background hue (e.g., `shadow-[0_8px_30px_rgba(14,30,37,0.12)]`), or use crisp `1px solid var(--border-color)` lines. 

**Rule 4: Interactive UI States**
* **Mandatory Generation:** LLMs naturally generate "static" successful states. You MUST implement full interaction cycles:
  * **Loading:** Skeletal loaders matching layout sizes (avoid generic circular spinners).
  * **Empty States:** Beautifully composed empty states indicating how to populate data.
  * **Error States:** Clear, inline error reporting (e.g., forms).
  * **Tactile Feedback:** On `:active`, use `-translate-y-[1px]` or `scale-[0.98]` to simulate a physical push indicating success/action.

**Rule 5: Data & Form Patterns**
* **Forms:** Label MUST sit above input. Helper text is optional but should exist in markup. Error text below input. Use a standard `gap-2` for input blocks.

## 4. CREATIVE PROACTIVITY (Anti-Slop Implementation)
To actively combat generic AI designs, systematically implement these high-end coding concepts as your baseline:
* **"Liquid Glass" Refraction:** When glassmorphism is needed, go beyond `backdrop-blur`. Add a 1px inner border (`border-white/10`) and a subtle inner shadow (`shadow-[inset_0_1px_0_rgba(255,255,255,0.1)]`) to simulate physical edge refraction.
* **Magnetic Micro-physics (If MOTION_INTENSITY > 5):** Implement buttons that pull slightly toward the mouse cursor using Framer Motion (mapping mouse coordinates to `useTransform` X/Y offsets), snapping back softly on `onMouseLeave`.
* **Staggered Orchestration:** Do not mount lists or grids instantly. Use `staggerChildren` (Framer) or CSS cascade (`animation-delay: calc(var(--index) * 100ms)`) to create sequential waterfall reveals. 

## 5. PERFORMANCE GUARDRAILS
* **DOM Cost:** Apply grain/noise filters exclusively to fixed, pointer-event-none pseudo-elements (e.g., `fixed inset-0 z-50 pointer-events-none`) and NEVER to scrolling containers to prevent continuous GPU repaints and mobile performance degradation.
* **Hardware Acceleration:** Never animate `top`, `left`, `width`, or `height`. Animate exclusively via `transform` and `opacity`.

## 6. PRE-FLIGHT CHECK
Evaluate your code against this matrix before output:
- [ ] Is global state used appropriately to avoid deep prop-drilling rather than arbitrarily?
- [ ] Is mobile layout collapse (`w-full`, `px-4`, `max-w-7xl mx-auto`) guaranteed for high-variance designs?
- [ ] Do `useEffect` animations contain strict cleanup functions?
- [ ] Are empty, loading, and error states provided?
- [ ] Are cards omitted in favor of spacing where possible?
