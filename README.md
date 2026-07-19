# eLearning

AIINOD-branded, single-file HTML widgets for Articulate Rise 360 embed blocks.

Every widget is self-contained — fonts, styles, JS inlined. No build step, no dependencies. Drop them into Rise via **Insert → Embed → iFrame**.

## Quick start

1. Copy a widget's hosted URL (e.g., `https://jhlburke-code.github.io/eLearning/widgets/tabbed-content/`).
2. In Rise: **Insert → Embed → iFrame**.
3. Paste the URL, set iframe height (table below), Save.

> GitHub Pages must be enabled on this repo first. Until then, preview widgets locally by opening `widgets/<name>/index.html` in a browser.

## Brand

| Role | Hex |
|---|---|
| Primary | `#1B3A6B` (AIINOD Navy) |
| Hover / Interactive | `#CC2229` (AIINOD Red) |
| Surface | `#F4F7FA` (AIINOD light-mode extension) |
| Accent / borders | `#0F2347` (AIINOD light-mode extension) |
| Typography | **Urbanist** (Google Fonts) |

## Folder structure

```
eLearning/
├── README.md
└── widgets/
    └── <kebab-name>/
        └── index.html   ← one self-contained widget per folder
```

## Iframe height guidance

| Widget complexity | Suggested `height=` |
|---|---|
| Static text / stat callout | 480–600 |
| Accordion (≤ 5 items) | 760–900 |
| Tabbed content (3–4 tabs) | 1180–1280 |
| Drag / spotlight | 1280+ |

## Accessibility

WCAG 2.1 AA throughout — full keyboard navigation (Tab / Arrow / Home / End for tabs), visible focus, ARIA roles (`tablist`, `tab`, `tabpanel`, `progressbar`, `region`).

## Completion signal

Every interactive widget emits a `postMessage` after the learner finishes:

```js
window.parent.postMessage({ type: 'complete' }, '*');
```

Rise marks the block complete in the learner's progress.

## Adding a new widget

1. `mkdir widgets/<kebab-name>`
2. Write `widgets/<kebab-name>/index.html` (single self-contained file).
3. Pick a unique scope ID like `custom-container-<kebab>-<version>`.
4. Commit: `feat(widgets): add <kebab-name>`
