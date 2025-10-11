# Graffiti

A minimal CSS framework with utilities that are actually useful.

## Install

### NPM Package

```bash
npm install @drop-in/graffiti
```

Then import in your project:

```js
import '@drop-in/graffiti'
```

### Copy & Paste

Download the CSS file directly:
```
https://raw.githubusercontent.com/stolinski/graffiti/refs/heads/main/drop-in.css
```

### CLI Tool

```bash
npx @drop-in/graffiti
```

This copies `drop-in.css` to your `src/` folder.

## Usage

### Typography

Fluid typography that scales automatically between viewport sizes:

```html
<h1 class="fs-xxxl">Extra Large</h1>
<h1>H1 - Large Heading</h1>
<h2>H2 - Med Heading</h2>
<h3>H3 - Small Heading</h3>
<p class="fs-xs">Extra small text</p>
```

**Custom fluid sizing:**
```html
<div style="--fl: 3">Scales like an h3</div>
```

**Container-based fluid text:**
```html
<div class="fc">
  <h1>Scales with container, not viewport</h1>
</div>
```

### Layouts

**Auto-fill card grid:**
```html
<div class="layout-card">
  <div>Card 1</div>
  <div>Card 2</div>
  <div>Card 3</div>
</div>
```

**Sidebar layout:**
```html
<div class="layout-sidebar">
  <aside>Sidebar (250px)</aside>
  <main>Main Content</main>
</div>

<!-- Variants: .narrow (150px), .wide (350px), .invert (sidebar on right) -->
```

**50/50 split:**
```html
<div class="layout-split">
  <div>Left Column</div>
  <div>Right Column</div>
</div>

<!-- Add .no-stack to stay side-by-side on mobile -->
```

**Three columns:**
```html
<div class="layout-three-col">
  <div>Column 1</div>
  <div>Column 2</div>
  <div>Column 3</div>
</div>
```

**Readable content container:**
```html
<div class="layout-readable center">
  <p>Optimal line length for readability</p>
  <div class="full-bleed">Breaks out to full width!</div>
</div>

<!-- Variants: .center, .end -->
```

**Holy Grail layout:**
```html
<div class="layout-holy-grail">
  <div style="width: 200px">Left sidebar</div>
  <div>Main content</div>
  <div style="width: 200px">Right sidebar</div>
</div>
```

**Stack (vertical spacing):**
```html
<div class="stack">
  <div>Item 1</div>
  <div>Item 2</div>
  <div>Item 3</div>
</div>
```

### Utilities

**Display utilities:**
```html
<div class="flex">Flexbox with gap</div>
<div class="grid">Grid with gap</div>
<div class="split">Space-between flex</div>
```

**Box styles:**
```html
<div class="box-1">Subtle box</div>
<div class="box-2">Semi-gloss box</div>
```

**Other utilities:**
```html
<ul class="no-list">Clean list</ul>
<div class="visually-hidden">Screen reader only</div>
<button class="circle">Icon</button>
```

### CSS Variables

**Customize layouts:**
```html
<div class="layout-card" style="--min-card-width: 250px; --gap: 1rem;">
  <!-- Cards with custom min-width and gap -->
</div>
```

**Use design tokens:**
```css
.custom-box {
  padding: var(--pad-m);
  border-radius: var(--br-s);
  box-shadow: var(--shadow-3);
  background: var(--tint-or-shade);
}
```

**Available variables:**
- Spacing: `--vs-s`, `--vs-base`, `--vs-m`, `--vs-l`
- Border radius: `--br-xs`, `--br-s`, `--br-m`, `--br-l`
- Padding: `--pad-xs`, `--pad-s`, `--pad-m`, `--pad-l`
- Shadows: `--shadow-1` through `--shadow-6`
- Colors: `--yellow`, `--orange`, `--red`, `--pink`, `--teal`, `--blue`
- Theme: `--fg`, `--bg`, `--tint-or-shade`, `--tint-or-shade-harder`

## Features

- **Fluid Typography**: Automatically scales between min/max viewport sizes
- **Container Queries**: Typography can respond to container width
- **Auto Dark Mode**: Uses `light-dark()` with `color-scheme`
- **Minimal & Composable**: Small footprint, mix and match classes
- **CSS Grid Layouts**: Modern, responsive layout system
- **Design Tokens**: Consistent spacing, shadows, and colors via CSS variables

## Documentation

Full documentation: https://drop-in-graffiti.netlify.app/

## License

ISC
