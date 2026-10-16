# Elementor MCP Performance Rules

> Production-grade Core Web Vitals guardrails and AI guidelines for building 95-100 PageSpeed WordPress pages with the Elementor Model Context Protocol (MCP).

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Elementor MCP](https://img.shields.io/badge/Elementor-MCP%20Ready-ff2a70.svg)](https://elementor.com/mcp/)
[![Core Web Vitals](https://img.shields.io/badge/Lighthouse-100%2F100-success.svg)](https://pagespeed.web.dev/)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](https://github.com)

---

## Overview

The **Elementor Model Context Protocol (MCP)** enables AI agents (Claude Code, Cursor, Antigravity, Codex) to build real, editable Elementor pages directly on WordPress.

However, leaving AI agents unguided often leads to classic website builder pitfalls:
- Deeply nested container soup (DOM bloat exceeding 1,500 nodes)
- Heavy carousels or autoplay videos above the fold, damaging Largest Contentful Paint (LCP)
- Media missing explicit dimensions, causing Cumulative Layout Shift (CLS)
- Uncontrolled Google Font requests that block rendering

This repository provides an automated **Performance Guardrail System** that constrains AI agents to build lightweight, atomic, Core-Web-Vitals-compliant Elementor structures from the very first prompt.

---

## Key Performance Pillars

1. **Flat DOM Hierarchy:** Strictly enforces Elementor V4 Flexbox Containers and CSS Grid. Container nesting is capped at 2 levels maximum. The legacy Spacer widget is banned in favor of native container gap and padding.
2. **Instant Hero Rendering (LCP < 1.2s):** Prohibits carousels, sliders, and video backgrounds in the first viewport. Prioritizes single optimized WebP/AVIF images with high priority loading.
3. **Zero Layout Shifts (CLS = 0):** Enforces explicit aspect-ratio and dimensions on all images and embeds. Requires `font-display: swap` across all typography rules.
4. **Asset Budgeting:** Limits font families to a maximum of 2, and font weights to at most 2 per family. Favors inline SVGs over bulky icon font libraries.
5. **Accessibility & SEO by Default:** Enforces strict sequential heading hierarchy (one single H1, followed by H2 and H3) and WCAG AA color contrast (4.5:1 minimum).

---

## Quickstart

### Option A: Using with Cursor
1. Clone or download this repository.
2. Copy the `.cursorrules` file into the root of your project workspace.
3. Open Cursor and connect your Elementor MCP tool. Cursor will automatically follow the performance rules on every prompt.

### Option B: Using with Antigravity / Gemini CLI
1. Copy `.gemini/rules/elementor-perf.md` into your local `.gemini/rules/` directory.
2. Antigravity will automatically inject these performance constraints when executing Elementor MCP actions.

### Option C: Using with Claude Desktop / Claude Code
1. Open [`prompts/system-prompt.md`](prompts/system-prompt.md).
2. Copy the system prompt into your Claude Project instructions or your initial conversation prompt.

---

## Repository Structure

```text
elementor-mcp-perf-rules/
├── .cursorrules                  # Rules configuration for Cursor AI
├── .gemini/
│   └── rules/
│       └── elementor-perf.md     # Rules configuration for Antigravity
├── prompts/
│   ├── system-prompt.md          # Universal AI system prompt
│   └── landing-page.md           # Example prompt for high-speed landing page
├── LICENSE                       # MIT License
├── README.md                     # English documentation
└── README.id.md                  # Dokumentasi Bahasa Indonesia
```

---

## Target Metrics

| Metric | Target | Focus Area |
| :--- | :--- | :--- |
| **LCP** (Largest Contentful Paint) | < 1.2s | Static hero, WebP format, high priority |
| **CLS** (Cumulative Layout Shift) | 0.00 | Locked aspect ratios, font-display: swap |
| **INP** (Interaction to Next Paint) | < 100ms | Lightweight DOM, minimal JavaScript |
| **DOM Size** | < 600 nodes | Maximum 2-level container nesting |
| **PageSpeed Score** | 95 - 100 | Clean code + server cache layer |

---

## Contributing

Contributions, feedback, and optimization techniques are warmly welcomed!
Feel free to open an issue or submit a pull request if you discover new patterns to enhance Elementor MCP performance.

---

## License

Released under the [MIT License](LICENSE).

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Elementor MCP](https://img.shields.io/badge/Elementor-MCP%20Ready-ff2a70.svg)](https://elementor.com/mcp/)
[![Core Web Vitals](https://img.shields.io/badge/Lighthouse-100%2F100-success.svg)](https://pagespeed.web.dev/)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](https://github.com)
[![M8ven Score](https://m8ven.ai/badge/mcp/andrean-lp/elementor-mcp-perf-rules-qfdwjz?s=2294086ae9b98788104c93fc1a6375840)](https://m8ven.ai/mcp/andrean-lp/elementor-mcp-perf-rules-qfdwjz?s=readme)
