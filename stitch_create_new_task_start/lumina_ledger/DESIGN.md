# Design System Specification: The Analytical Architect

## 1. Overview & Creative North Star
**Creative North Star: "Precision Transparency"**

This design system rejects the "cluttered dashboard" trope of traditional banking software. Instead, it adopts the ethos of a high-end editorial publication—where data is not just displayed, but curated. We move beyond "Modern Minimalist" into a realm of **Precision Transparency**, utilizing layered surfaces, intentional white space, and a sophisticated typographic scale to make complex SQL visualizations feel effortless and authoritative.

The system breaks the "template" look by avoiding rigid 1px containment. We leverage **tonal depth** and **asymmetric density** to guide the eye. By utilizing a "Glass & Paper" metaphor, we treat the UI as a series of physical, semi-transparent layers that provide a sense of depth and focus, ensuring that even the most data-dense SQL tables remain legible and non-intimidating.

---

## 2. Colors & Surface Philosophy

### The "No-Line" Rule
To achieve a premium, custom feel, **1px solid borders are prohibited for sectioning.** Structural boundaries must be defined through background shifts. For example, a query editor (Surface Container Low) sitting on the main workspace (Surface) creates a boundary through tone rather than a stroke.

### Surface Hierarchy & Nesting
Treat the UI as a series of stacked sheets. Use the `surface-container` tiers to define "Importance Nesting":
- **Base Layer:** `surface` (#f7fafc) – The main canvas.
- **Sectioning:** `surface-container-low` (#f1f4f6) – For sidebars or utility panels.
- **Content Cards:** `surface-container-lowest` (#ffffff) – For the primary data tables to ensure maximum contrast.
- **Interactions:** `surface-container-high` (#e5e9eb) – For active states or hovered elements.

### Glass & Gradient Signature
- **Glassmorphism:** Use `surface_variant` at 60% opacity with a `20px` backdrop-blur for floating modals or dropdown menus. This ensures the data beneath is felt, but not distracting.
- **The Signature Gradient:** For primary actions, transition from `primary` (#00346f) to `primary_container` (#004a99) at a 135-degree angle. This adds a "visual soul" to the professional blue, preventing it from feeling like a generic bank template.

---

## 3. Typography: The Editorial Engine

We utilize a dual-typeface system to balance authority with utility.

*   **Display & Headlines (Manrope):** Chosen for its geometric precision and modern "tech-banking" feel. Use `display-sm` or `headline-md` for page titles and high-level metrics to command attention.
*   **Data & Utility (Inter):** The workhorse. Inter’s tall x-height makes it perfect for high-density SQL results and code snippets.

**Hierarchy as Brand:**
- **Primary Data Points:** Use `title-lg` in `on_surface`.
- **Table Headers:** Use `label-md` in `on_surface_variant`, all-caps with `0.05rem` letter spacing.
- **SQL Syntax:** Use `body-sm` with a monospace fallback to ensure alignment.

---

## 4. Elevation & Depth

### The Layering Principle
Depth is achieved through **Tonal Layering** rather than structural shadows.
- Place a `surface-container-lowest` card on a `surface-container-low` background. The difference in hex value provides a "soft lift" that feels architectural.

### Ambient Shadows
Shadows are reserved for elements that physically "float" above the logic (Modals, Tooltips).
- **Style:** Blur: `24px`, Spread: `-4px`, Opacity: `6%`.
- **Tinting:** The shadow color must be `on_surface` (#181c1e), never pure black, to maintain a soft, ambient light effect.

### The "Ghost Border" Fallback
In high-density data tables where separation is critical for accessibility, use the **Ghost Border**:
- `outline-variant` (#c2c6d3) at **15% opacity**. This provides a guide for the eye without creating visual "noise."

---

## 5. Components

### Data Tables (The Core)
*   **The Container:** No outer border. Use `surface-container-lowest` for the table body.
*   **Rows:** Forbid dividers. Use a subtle `surface-container-low` background on `:hover`. 
*   **Cell Spacing:** Use `spacing-3` (0.6rem) for vertical padding to maintain density while allowing the "Inter" typeface to breathe.
*   **Column Headers:** Sticky positioning with a `surface_variant` (60% opacity) glassmorphism effect.

### Action Buttons
*   **Primary:** Gradient (Primary to Primary-Container), `rounded-md` (0.375rem). No shadow.
*   **Secondary:** `surface-container-highest` background with `on_surface` text.
*   **Tertiary:** Transparent background, `on_primary_fixed_variant` text, with a `0.5` spacing underline on hover.

### Tab Bars (Workspace Navigation)
*   Avoid the "folder tab" look. Use a minimalist underline approach.
*   **Active State:** `primary` color bar, 2px thick, positioned at the bottom of the tab.
*   **Inactive State:** `on_surface_variant` text.
*   **Background:** Use `surface-container-low` to differentiate the navigation area from the data workspace.

### SQL Input Fields
*   **Container:** `surface-container-highest` with a `rounded-sm` (0.125rem) corner.
*   **Focus State:** A 2px "Ghost Border" using `primary` at 40% opacity. 
*   **Typography:** Use `body-md` for the query text.

---

## 6. Do’s and Don’ts

### Do
*   **DO** use asymmetry in your layout. Align your SQL editor to the left and results to the right, but allow the results pane to take up 70% of the horizontal "breathing room."
*   **DO** use `spacing-8` and `spacing-10` for major section margins. White space is a functional tool for clarity, not "wasted" space.
*   **DO** use `tertiary` (#5f2200) sparingly for "Warning" or "Pending" states to provide a sophisticated alternative to "Standard Orange."

### Don’t
*   **DON’T** use 100% opaque, high-contrast dividers. If you feel the need for a line, try a background color shift first.
*   **DON’T** use `rounded-full` for anything other than status chips. We want the tool to feel like a precision instrument; "pill" buttons feel too consumer-facing.
*   **DON’T** crowd the table cells. If the data is dense, increase the `surface` contrast rather than shrinking the font size. Never go below `body-sm` (0.75rem).