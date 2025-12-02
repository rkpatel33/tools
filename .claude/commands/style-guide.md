# Web Tools Style Guide

Use this style guide when creating or modifying HTML tools in this repository.

## Design System

Based on Vercel Geist with Claude app influences.

## Colors

### Backgrounds
```css
--background: #0a0a0a;           /* Primary dark background */
--background-secondary: #111111;  /* Cards, panels */
--background-interactive: #262626; /* Buttons, inputs */
--background-hover: #333333;      /* Hover states */
```

### Accent Colors
```css
--blue-500: #0070f3;    /* Primary actions */
--blue-600: #0060d1;    /* Primary hover */
```

### Text
```css
--text-primary: #ededed;   /* Main text */
--text-secondary: #a1a1a1; /* Muted text, labels */
```

### Borders
```css
--border: #262626;  /* Subtle borders */
```

## Buttons

### Icon-Only Circular Buttons (Preferred)
```css
button {
    background: #262626;
    color: #ffffff;
    border: none;
    width: 44px;
    height: 44px;
    border-radius: 22px;
    cursor: pointer;
    transition: all 0.15s ease;
    display: flex;
    align-items: center;
    justify-content: center;
    padding: 0;
}

button:hover {
    background: #333333;
}

button:active {
    transform: scale(0.95);
    opacity: 0.9;
}

button.primary {
    background: #0070f3;
}

button.primary:hover {
    background: #0060d1;
}

button:disabled {
    opacity: 0.4;
    cursor: not-allowed;
}
```

### Button Row Layout
```css
.button-row {
    display: flex;
    gap: 12px;
    justify-content: center;
    align-items: center;
}
```

## Icons

Use Heroicons (outline style). Key specs:
- **Size**: 20x20px inside 44px buttons
- **Stroke width**: 1.5 (not 2 - thinner is cleaner)
- **Style**: outline, not solid

```html
<button title="Action Name">
    <svg fill="none" stroke="currentColor" viewBox="0 0 24 24">
        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="..."></path>
    </svg>
</button>
```

```css
button svg {
    width: 20px;
    height: 20px;
}
```

Always include `title` attribute for accessibility.

## Dropdowns/Selects

```css
select {
    background: #262626;
    color: #a1a1a1;
    border: none;
    padding: 10px 28px 10px 12px;
    border-radius: 22px;
    font-size: 12px;
    font-weight: 500;
    cursor: pointer;
    appearance: none;
    -webkit-appearance: none;
    background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' fill='none' viewBox='0 0 24 24' stroke='%23a1a1a1'%3E%3Cpath stroke-linecap='round' stroke-linejoin='round' stroke-width='2' d='M19 9l-7 7-7-7'/%3E%3C/svg%3E");
    background-repeat: no-repeat;
    background-position: right 10px center;
    background-size: 12px;
    height: 36px;
}

select:hover {
    background-color: #333333;
}

select:focus {
    outline: none;
}
```

## iOS PWA Configuration

Add to `<head>` for home screen support:

```html
<!-- iOS PWA Configuration -->
<meta name="apple-mobile-web-app-capable" content="yes">
<meta name="apple-mobile-web-app-status-bar-style" content="black-translucent">
<meta name="apple-mobile-web-app-title" content="App Name">
<link rel="apple-touch-icon" href="icons/app-icon.png">

<!-- Android PWA Configuration -->
<meta name="mobile-web-app-capable" content="yes">
<meta name="theme-color" content="#0a0a0a">
```

App icons should be 180x180px PNG.

## Corner Handles (for draggable points)

```css
.corner-handle {
    width: 22px;
    height: 22px;
    background: #0070f3;
    border: 2px solid #ffffff;
    border-radius: 50%;
    position: absolute;
    transform: translate(-50%, -50%);
    cursor: grab;
    pointer-events: auto;
    touch-action: none;
    box-shadow: 0 2px 6px rgba(0, 0, 0, 0.4);
}

.corner-handle:active {
    cursor: grabbing;
    background: #0060d1;
}
```

## Overlay Polygons

```html
<polygon fill="rgba(0, 112, 243, 0.2)" stroke="#0070f3" stroke-width="1.5"/>
```

## Typography

```css
body {
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
}

h1 { font-size: 18px; font-weight: 600; }
.status { font-size: 13px; color: #a1a1a1; }
```

## Spacing

- Button gap: 12px
- Control padding: 12px 16px
- Section borders: 1px solid #262626

## Mobile Viewport

```html
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
```

```css
body {
    min-height: 100vh;
    min-height: -webkit-fill-available;
    overflow: hidden;
    touch-action: none;
}
```

## Common Icon Paths (Heroicons)

### Camera (still photo)
```
M3 9a2 2 0 012-2h.93a2 2 0 001.664-.89l.812-1.22A2 2 0 0110.07 4h3.86a2 2 0 011.664.89l.812 1.22A2 2 0 0018.07 7H19a2 2 0 012 2v9a2 2 0 01-2 2H5a2 2 0 01-2-2V9z
M15 13a3 3 0 11-6 0 3 3 0 016 0z
```

### Video Camera
```
M15 10l4.553-2.276A1 1 0 0121 8.618v6.764a1 1 0 01-1.447.894L15 14M5 18h8a2 2 0 002-2V8a2 2 0 00-2-2H5a2 2 0 00-2 2v8a2 2 0 002 2z
```

### Checkmark
```
M5 13l4 4L19 7
```

### X (Close)
```
M6 18L18 6M6 6l12 12
```

### Download
```
M4 16v1a3 3 0 003 3h10a3 3 0 003-3v-1m-4-4l-4 4m0 0l-4-4m4 4V4
```

### Upload/Image
```
M4 16l4.586-4.586a2 2 0 012.828 0L16 16m-2-2l1.586-1.586a2 2 0 012.828 0L20 14m-6-6h.01M6 20h12a2 2 0 002-2V6a2 2 0 00-2-2H6a2 2 0 00-2 2v12a2 2 0 002 2z
```

### Refresh/Retry
```
M4 4v5h.582m15.356 2A8.001 8.001 0 004.582 9m0 0H9m11 11v-5h-.581m0 0a8.003 8.003 0 01-15.357-2m15.357 2H15
```

### Plus
```
M12 4v16m8-8H4
```

### Share
```
M8.684 13.342C8.886 12.938 9 12.482 9 12c0-.482-.114-.938-.316-1.342m0 2.684a3 3 0 110-2.684m0 2.684l6.632 3.316m-6.632-6l6.632-3.316m0 0a3 3 0 105.367-2.684 3 3 0 00-5.367 2.684zm0 9.316a3 3 0 105.368 2.684 3 3 0 00-5.368-2.684z
```
