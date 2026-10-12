# Elementor MCP Performance Guardrails for Antigravity & AI Agents

When interacting with WordPress via the Elementor Model Context Protocol (MCP), enforce these performance standards on every generated block, page, or container.

## Core Directives

1. **Flat Layout Hierarchy (DOM Efficiency)**
   - Utilize Elementor V4 Flexbox Containers and CSS Grid only.
   - Restrict container nesting depth to maximum 2 levels.
   - Use container `gap` and `padding` for spacing; omit empty Spacer widgets.

2. **LCP & Hero Section Rules**
   - The first viewport (Hero) must render within 1.2s.
   - Do not generate carousels, nested sliders, or video backgrounds above the fold.
   - Primary hero image must be WebP/AVIF format and marked for high priority loading.

3. **Zero Cumulative Layout Shift (CLS = 0)**
   - Always supply explicit aspect ratios or width/height attributes for media elements.
   - Ensure typography utilizes `font-display: swap`.

4. **Resource Budget**
   - Maximum 2 font families (Headings and Body).
   - Maximum 2 font weights per family.
   - Prefer SVG icons over heavy font icon libraries.

5. **Semantic & Accessibility Compliance**
   - Exactly one H1 per page.
   - Sequential headings (H2 -> H3 -> H4).
   - High contrast colors (WCAG AA ratio 4.5:1 minimum).
   - Descriptive alt text on all images.
