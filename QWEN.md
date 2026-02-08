# Carousel Project - QWEN Context

## Project Overview

**CaruselFun** is a web application for generating Instagram carousels from JSON structures. It allows users to create beautiful carousel presentations with previews, theming options, typography controls, and export capabilities to JPG/ZIP formats.

The application is built as a single HTML file with embedded JavaScript and CSS, making it lightweight and easy to deploy. It features a modern UI with gradient backgrounds, glass-morphism panels, and responsive design.

### Key Features

1. **JSON Input Processing**: Accepts structured JSON input with title and slides
2. **Visual Preview**: Real-time preview of carousel slides
3. **Theming Options**: Multiple layout and color palette options
4. **Typography Controls**: Support for styled text with `<accent>` and `<bold>` tags
5. **Image Integration**: Ability to add images to slides with different positioning modes
6. **Export Functionality**: Download slides as individual JPGs or ZIP archive
7. **Responsive Design**: Works on both desktop and mobile devices

### Technical Architecture

- **Single Page Application**: Entire application contained in `index.html`
- **Canvas Rendering**: Uses HTML5 Canvas for slide generation
- **Client-Side Processing**: All processing happens in the browser
- **External Library**: Uses JSZip library for ZIP archive creation

## Building and Running

The application is a standalone HTML file that can be opened directly in any modern browser:

1. Open `index.html` in a web browser
2. No build process required
3. No server needed - works completely client-side

### Development Setup

Since this is a single HTML file with embedded JavaScript and CSS:

1. Edit the `index.html` file directly
2. Refresh the browser to see changes
3. Use browser developer tools for debugging

### Testing

Manual testing can be performed by:
1. Using the JSON input functionality
2. Verifying all UI elements work correctly
3. Testing export functionality
4. Checking responsive behavior on different screen sizes

## Development Conventions

### Code Structure

The application follows a single-file architecture with three main sections:
1. HTML structure and styling in the `<head>` and `<body>` tags
2. JavaScript logic in the `<script>` tag at the end of the body
3. Global state management using the `state` object

### JavaScript Patterns

- **Global State Management**: Uses a central `state` object to manage application state
- **Event-Driven Architecture**: UI interactions trigger event handlers
- **Canvas Drawing**: Custom drawing functions for slide generation
- **JSON Parsing**: Robust JSON parsing with error handling and sanitization
- **Responsive Design**: Mobile-first approach with media queries

### UI Components

- **Glass-morphism Panels**: Modern UI with transparency and blur effects
- **Theme Pickers**: Layout and color palette selection with visual previews
- **Preview Cards**: Canvas-based slide previews with click interactions
- **Modal Dialogs**: Image selection interface with positioning options

### Styling Approach

- **CSS Variables**: Defines color scheme and theme variables in `:root`
- **Modern CSS**: Uses Grid, Flexbox, and modern layout techniques
- **Responsive Design**: Media queries for mobile adaptation
- **Imported Fonts**: Google Fonts integration for typography options

## Key Functions

### Core Functionality

- `drawSlide()`: Main function for rendering slides on canvas
- `normalizeAiResult()`: Processes and validates JSON input
- `renderPreviews()`: Updates the preview grid with current slides
- `downloadZip()`: Creates and downloads ZIP archive of slides
- `buildPrompt()`: Generates AI prompt template for JSON creation

### State Management

- `applyStateFromInputs()`: Updates global state from UI controls
- `sanitizeJsonInput()`: Cleans and prepares JSON input for parsing
- `parseStyledSegments()`: Processes text with markup tags

### UI Interactions

- Event listeners for all form controls and buttons
- Modal dialog management for image selection
- Real-time preview updates
- Copy-to-clipboard functionality for AI prompts

## File Structure

```
Carousel/
├── index.html          # Main application file (HTML + CSS + JS)
├── README.md           # Project description
├── .gitignore          # Git ignore rules
└── .git/               # Git repository metadata
```

## Dependencies

- **JSZip**: External library for ZIP file creation (loaded from CDN)
- **Google Fonts**: Typography options loaded from external service
- **Modern Browser APIs**: Canvas, Clipboard API, FileReader, etc.

## Export Formats

The application supports exporting slides in two formats:
1. Individual JPG files (for mobile browsers)
2. ZIP archive containing all JPG files (for desktop browsers)

## Supported Dimensions

- 800 × 1000
- 1080 × 1080 (square)
- 1080 × 1920 (portrait)
- 1350 × 1080 (landscape)

## Color Palettes

- Linen
- Ice
- Sand
- Mint
- Rose
- Midnight

## Layout Options

- Line
- Frame
- Split
- Grid
- Pill
- Corner

## Typography Options

- Golos Text
- Manrope
- Inter
- Rubik
- Montserrat