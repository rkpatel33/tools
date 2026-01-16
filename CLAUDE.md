# Tools

A collection of single-page HTML/CSS/JS tools hosted on GitHub Pages.

## Research Tips

When referencing external libraries or documentation:
- **Clone repos to `/tmp`** for detailed reference (e.g., `git clone https://github.com/user/repo /tmp/repo`) - this is more reliable than fetching GitHub pages directly
- **Online docs** are fine for quick reference when you just need API signatures or basic usage examples

## Commit Checklist

When committing changes to HTML tools, **always update README.md** with links to the deployed tools:
- Format: `<a href="https://rkpatel33.github.io/tools/tool-name.html" target="_blank">Tool Name</a>`
- Links must open in new tabs (`target="_blank"`)

## Project Structure

- Each tool is a standalone `.html` file in the root directory
- Tools are self-contained with inline CSS and JS
- No build step required - push to `master` to deploy
- Live at: https://rkpatel33.github.io/tools/

## Adding a New Tool

1. Create `tool-name.html` in the root
2. Use the visual style guide below for consistency
3. Add a link to `README.md` (must open in new tab)
4. Commit and push to `master`

---

## Previewing HTML from Branches

To preview HTML files before merging to master, use **htmlpreview.github.io**:

```
https://htmlpreview.github.io/?https://github.com/rkpatel33/tools/blob/{branch-name}/{file}.html
```

Example:
```
https://htmlpreview.github.io/?https://github.com/rkpatel33/tools/blob/claude/my-feature-branch/tool-name.html
```

---

## CDN Libraries

Plain JS libraries that can be loaded directly from CDN (no build step):

### Charts & Visualization
- **uPlot** (~45KB) - Fast time series charts, ideal for streaming/real-time data
  ```html
  <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/uplot@1.6.31/dist/uPlot.min.css">
  <script src="https://cdn.jsdelivr.net/npm/uplot@1.6.31/dist/uPlot.iife.min.js"></script>
  ```
  [Demos](https://leeoniya.github.io/uPlot/demos/index.html) | [GitHub](https://github.com/leeoniya/uPlot)

- **Chart.js** (~200KB) - Simple, flexible charts with many chart types
  ```html
  <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
  ```
  [Docs](https://www.chartjs.org/)

- **ApexCharts** - Modern charts with annotations support
  ```html
  <script src="https://cdn.jsdelivr.net/npm/apexcharts"></script>
  ```

---

## Visual Style Guide

Based on [Vercel Geist Design System](https://vercel.com/geist/introduction).

### Typography

**Font Stack:**
```css
font-family: 'Geist', -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, sans-serif;
font-family: 'Geist Mono', 'SF Mono', Consolas, 'Liberation Mono', Menlo, monospace; /* for code */
```

**Loading Geist fonts (optional):**
```html
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/geist@1.3.0/dist/fonts/geist-sans/style.css">
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/geist@1.3.0/dist/fonts/geist-mono/style.css">
```

**Sizes:**
- Headings: 48px, 32px, 24px, 20px, 16px
- Body/Copy: 16px (default), 14px (small)
- Labels: 14px, 13px, 12px
- Line height: 1.5 for body, 1.2 for headings

### Colors

**Backgrounds:**
```css
--background: #ffffff;        /* light mode */
--background-secondary: #fafafa;
--background: #0a0a0a;        /* dark mode */
--background-secondary: #111111;
```

**Grays (light mode):**
```css
--gray-100: #f7f7f7;
--gray-200: #e5e5e5;
--gray-300: #d4d4d4;
--gray-400: #a3a3a3;
--gray-500: #737373;
--gray-600: #525252;
--gray-700: #404040;
--gray-800: #262626;
--gray-900: #171717;
--gray-1000: #0a0a0a;
```

**Accent Colors:**
```css
--blue-700: #0070f3;          /* primary actions */
--blue-800: #0060d1;          /* hover state */
--red-700: #e5484d;           /* errors, destructive */
--green-700: #46a758;         /* success */
--amber-700: #f5a623;         /* warnings */
```

**Text:**
```css
--text-primary: #171717;      /* light mode */
--text-secondary: #666666;
--text-primary: #ededed;      /* dark mode */
--text-secondary: #a1a1a1;
```

### Spacing

Use multiples of 4px:
- `4px` - tight
- `8px` - compact
- `12px` - default inner padding
- `16px` - standard spacing
- `20px` - comfortable
- `24px` - section spacing
- `32px` - large gaps
- `40px` - page margins

### Border Radius

```css
--radius-sm: 4px;   /* buttons, inputs */
--radius-md: 8px;   /* cards, panels */
--radius-lg: 12px;  /* modals, large containers */
--radius-full: 9999px; /* pills, avatars */
```

### Shadows

```css
--shadow-sm: 0 1px 2px rgba(0, 0, 0, 0.05);
--shadow-md: 0 2px 4px rgba(0, 0, 0, 0.1);
--shadow-lg: 0 4px 8px rgba(0, 0, 0, 0.1);
```

### Icons

Use [Heroicons](https://heroicons.com/) for all iconography. Copy SVG directly inline:

```html
<!-- Example: Camera icon (outline style, 24x24) -->
<svg fill="none" stroke="currentColor" viewBox="0 0 24 24">
    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 9a2 2 0 012-2h.93a2 2 0 001.664-.89l.812-1.22A2 2 0 0110.07 4h3.86a2 2 0 011.664.89l.812 1.22A2 2 0 0018.07 7H19a2 2 0 012 2v9a2 2 0 01-2 2H5a2 2 0 01-2-2V9z"></path>
    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 13a3 3 0 11-6 0 3 3 0 016 0z"></path>
</svg>
```

Icon sizing in buttons:
```css
button svg {
    width: 16px;
    height: 16px;
}
```

### Component Patterns

**Buttons:**
```css
button {
    background: #171717;
    color: #ffffff;
    border: none;
    padding: 8px 16px;
    border-radius: 6px;
    font-size: 14px;
    font-weight: 500;
    cursor: pointer;
    transition: background 0.15s ease;
}
button:hover {
    background: #333333;
}
```

**Inputs:**
```css
input, textarea {
    width: 100%;
    padding: 10px 12px;
    border: 1px solid #e5e5e5;
    border-radius: 6px;
    font-size: 14px;
    background: #ffffff;
    transition: border-color 0.15s ease;
}
input:focus, textarea:focus {
    outline: none;
    border-color: #171717;
}
```

**Cards/Panels:**
```css
.panel {
    background: #ffffff;
    border: 1px solid #e5e5e5;
    border-radius: 8px;
    padding: 20px;
}
```

### Starter Template

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Tool Name</title>
    <style>
        * { box-sizing: border-box; margin: 0; padding: 0; }

        body {
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
            background: #fafafa;
            color: #171717;
            padding: 20px;
            min-height: 100vh;
        }

        .container {
            max-width: 600px;
            margin: 0 auto;
        }

        h1 {
            font-size: 24px;
            font-weight: 600;
            margin-bottom: 20px;
        }

        .panel {
            background: #ffffff;
            border: 1px solid #e5e5e5;
            border-radius: 8px;
            padding: 20px;
        }

        input, textarea {
            width: 100%;
            padding: 10px 12px;
            border: 1px solid #e5e5e5;
            border-radius: 6px;
            font-size: 14px;
            margin-bottom: 12px;
        }

        input:focus, textarea:focus {
            outline: none;
            border-color: #171717;
        }

        button {
            background: #171717;
            color: #ffffff;
            border: none;
            padding: 10px 20px;
            border-radius: 6px;
            font-size: 14px;
            font-weight: 500;
            cursor: pointer;
        }

        button:hover {
            background: #333333;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Tool Name</h1>
        <div class="panel">
            <!-- Tool content here -->
        </div>
    </div>

    <script>
        // Tool logic here
    </script>
</body>
</html>
```
