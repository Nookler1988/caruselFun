# AGENTS.md - CaruselFun

Guidelines for AI agents working on this Instagram carousel generator.

## Project Overview

Single-file HTML application with embedded CSS and JavaScript. No build tools, bundlers, or frameworks. Uses vanilla HTML5 Canvas for image generation.

## Build/Test/Lint Commands

**No build system** - This is a vanilla HTML/CSS/JS project.

- **Development**: Open `index.html` directly in browser
- **Preview**: `python -m http.server 8000` or `npx serve` (optional)
- **Testing**: Manual testing only - test export, JSON parsing, responsive layout
- **No linting configured**: Follow code style guidelines below

## Code Style Guidelines

### File Organization

Maintain single-file architecture:
1. `<head>`: CSS styles in `<style>` tag
2. `<body>`: HTML structure
3. End of `<body>`: JavaScript in `<script>` tag

### CSS Conventions

- **CSS Variables**: Define in `:root` for colors, use semantic names
  ```css
  --bg-1: #0b0f19;
  --accent-1: #00d4ff;
  --text: #f5f7ff;
  ```
- **Glass-morphism**: Use `backdrop-filter: blur()` with rgba backgrounds
- **Responsive**: Mobile-first with `@media (max-width: 780px)` breakpoints
- **Naming**: Use BEM-like naming (`.panel-head`, `.preview-card`)

### JavaScript Conventions

- **State Management**: Use global `state` object
  ```javascript
  const state = {
    slides: [],
    size: { w: 1080, h: 1080 },
    // ...
  };
  ```
- **Functions**: camelCase, descriptive names
  ```javascript
  function drawSlide(canvas, text, index) { }
  function normalizeAiResult(result) { }
  ```
- **Event Handlers**: Add at end of script, use arrow functions
  ```javascript
  downloadBtn.addEventListener("click", () => { });
  ```
- **Canvas**: Always set dimensions before drawing
  ```javascript
  canvas.width = w;
  canvas.height = h;
  const ctx = canvas.getContext("2d");
  ```

### HTML Conventions

- **Language**: Russian content, English code
- **IDs**: camelCase matching JS variables
- **Accessibility**: Add `aria-hidden` to modals
- **CDN Libraries**: Load at end before closing `</body>`

### Error Handling

```javascript
try {
  const parsed = JSON.parse(raw);
} catch (err) {
  console.error("JSON Parse Error:", err);
  alert("Некорректный JSON.");
  return;
}
```

### Mobile-First Features

When adding save/download features:
1. Check `isMobileDevice()` and `isIOS()` for platform detection
2. Use Web Share API on Android (`navigator.share`)
3. Use blob URLs for iOS long-press support
4. Provide fallbacks for unsupported browsers

### Adding New Features

1. Define data structures in `state` object
2. Create rendering function if needed
3. Add UI elements to HTML
4. Attach event listeners at script end
5. Update `renderPreviews()` if UI needs refresh
6. Test on both mobile and desktop

### Git Workflow

```bash
git add index.html
git commit -m "feat: description"
git push origin gh-pages
```

Branch: `gh-pages` (GitHub Pages deployment)

## Key Dependencies

- JSZip (CDN): ZIP file creation
- heic-to (CDN): HEIC image conversion
- Google Fonts: Typography

## Testing Checklist

- [ ] JSON input works correctly
- [ ] Canvas renders without errors
- [ ] Mobile responsive layout
- [ ] Download/Save buttons work on iOS
- [ ] Download/Save buttons work on Android
- [ ] ZIP export works on desktop
- [ ] No console errors

## Naming Conventions

### Functions
- Use camelCase: `drawSlide()`, `normalizeAiResult()`
- Descriptive names indicating purpose
- Event handlers: `handleClick`, `onSubmit`

### Variables
- camelCase: `state`, `currentIndex`, `blobUrl`
- Constants: UPPER_SNAKE_CASE for true constants
- CSS classes: kebab-case: `.preview-card`, `.step-panel`

### IDs
- camelCase matching JavaScript variables
- Examples: `jsonInput`, `downloadBtn`, `slideImageInput`

## Code Patterns

### State Updates
Always update state before re-rendering:
```javascript
applyStateFromInputs();
state.title = normalized.title;
renderPreviews();
```

### Canvas Operations
```javascript
const canvas = document.createElement("canvas");
canvas.width = w;
canvas.height = h;
const ctx = canvas.getContext("2d");
// Draw operations...
const blob = await new Promise(resolve => 
  canvas.toBlob(resolve, 'image/jpeg', 0.92)
);
```

### Platform Detection
```javascript
function isMobileDevice() {
  return /Mobi|Android|iPhone|iPad|iPod/i.test(navigator.userAgent);
}

function isIOS() {
  return /iPad|iPhone|iPod/.test(navigator.userAgent) && !window.MSStream;
}
```
</content>