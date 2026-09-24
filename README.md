# ChromaSphere

![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=flat-square&logo=html5&logoColor=white) ![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=flat-square&logo=css3&logoColor=white) ![JavaScript](https://img.shields.io/badge/JavaScript-ES6%2B-F7DF1E?style=flat-square&logo=javascript&logoColor=111111) ![Canvas API](https://img.shields.io/badge/Canvas-API-2C2C2C?style=flat-square) ![Responsive](https://img.shields.io/badge/Responsive-Design-6B7280?style=flat-square)

**ChromaSphere** is a lightweight, interactive color picker built with vanilla HTML, CSS, and JavaScript. It combines a programmatically rendered HSL color wheel with direct HEX input, RGB information, live color preview, and dynamic background updates.

The project is designed as a simple, dependency-free implementation of an interactive color selection interface using the native Canvas API.

---

## Overview

ChromaSphere provides two ways to select a color:

1. Select a color directly from the interactive color wheel.
2. Enter a six-digit HEX color manually.

The selected color is immediately reflected throughout the interface. The page background, color preview, RGB information, ambient glow, and selection indicator are updated dynamically.

---

## Features

### Color Selection

- Interactive circular HSL color wheel
- Click-to-select color interaction
- Drag interaction for continuous color selection
- Touch support for mobile devices
- Real-time color selection feedback
- Visual selection indicator

### Color Input

- Direct six-digit HEX input
- Automatic uppercase formatting
- Real-time input handling
- HEX validation
- Automatic synchronization between manual input and the color wheel

### Color Information

- HEX color representation
- RGB value display
- Live color preview
- Automatic contrast calculation for the selector

### Interface

- Responsive layout
- Dark interface
- Glass-style UI panels
- Subtle ambient background glow
- Smooth color transitions
- Entrance animations
- Mobile-friendly touch interaction

### Technical

- No frameworks
- No JavaScript dependencies
- No build system
- No package installation
- Uses the native HTML Canvas API
- Entire application contained in a single HTML file

---

## How It Works

### Color Wheel Rendering

The color wheel is generated dynamically using the HTML Canvas API.

For every pixel inside the circular canvas, ChromaSphere calculates its position relative to the center:

```text
Angle from center      → Hue
Distance from center   → Saturation
Fixed value            → Lightness
```

The application uses an HSL model with a fixed lightness of `50%`.

The resulting HSL value is converted to RGB before being written to the canvas.

### Color Selection

When the user interacts with the wheel, the application:

1. Calculates the cursor or touch position relative to the canvas.
2. Determines the corresponding pixel.
3. Reads the pixel's RGB values from the canvas.
4. Converts the RGB value to HEX.
5. Updates the active color across the interface.

### HEX Input

Users can enter a HEX value directly into the input field.

For example:

```text
FFFFFF
6366F1
E11D48
22C55E
```

When a valid six-digit HEX value is entered, ChromaSphere updates:

- Background color
- Color preview
- RGB information
- Selection indicator
- Ambient background glow

### Selector Positioning

When a color is entered manually, the application searches the rendered color wheel for the closest matching RGB value.

The search uses sampled canvas pixels to avoid performing an exhaustive search over every pixel, keeping the lookup relatively lightweight.

---

## Technologies

| Technology        | Purpose                                           |
| ----------------- | ------------------------------------------------- |
| HTML5             | Application structure                             |
| CSS3              | Layout, styling, animations and responsive design |
| JavaScript        | Application logic and interaction                 |
| Canvas API        | Dynamic color wheel rendering                     |
| HSL               | Color wheel generation                            |
| RGB               | Pixel-level color representation                  |
| HEX               | User-facing color input                           |
| Plus Jakarta Sans | Interface typography                              |

---

## Project Structure

```text
ChromaSphere/
└── index.html
```

The application is intentionally self-contained. All HTML, CSS, and JavaScript are currently included in `index.html`.

---

## Getting Started

### Requirements

A modern web browser with support for:

- HTML5 Canvas
- ES6+ JavaScript
- CSS3
- Touch Events
- Backdrop Filter

No additional software or dependencies are required.

### Run Locally

Clone the repository:

```bash
git clone https://github.com/your-username/chromasphere.git
```

Navigate into the project:

```bash
cd chromasphere
```

Open `index.html` in your browser.

Alternatively, the file can be opened directly without a local development server.

---

## Interaction

### Desktop

- **Click** inside the color wheel to select a color.
- **Click and drag** to continuously select colors.
- **Type a HEX value** into the input field to set a specific color.

### Mobile

- **Tap** the color wheel to select a color.
- **Touch and drag** across the wheel to continuously select colors.
- **Enter a HEX value** using the input field.

---

## Color Conversion

ChromaSphere implements its own color conversion functions rather than relying on an external color library.

The application supports the following conversions:

```text
HSL → RGB
RGB → HEX
HEX → RGB
```

This keeps the project dependency-free and makes the underlying color calculations easy to inspect and understand.

---

## Design

The interface uses a dark visual system with translucent panels, subtle borders, soft shadows, and restrained animations.

The design focuses on keeping the color itself as the primary visual element while the surrounding interface remains intentionally minimal.

The page background also responds to the selected color, creating a dynamic relationship between the picker and the interface.

---

## Performance Considerations

The color wheel is generated once using `ImageData` and written directly to the canvas.

For manually entered colors, the selector-position lookup uses sampled pixels rather than scanning every pixel in the canvas.

The application also uses:

```javascript
getContext("2d", {
  willReadFrequently: true,
});
```

which is appropriate for the frequent pixel-reading operations performed during color selection.

---

## Current Limitations

- Only HEX input is currently supported directly.
- The color wheel uses a fixed lightness value of `50%`.
- No persistent color history is currently implemented.
- Selected colors are not stored between sessions.
- Color palette generation is not currently included.
- The project currently has no external component or utility library.

---

## Potential Improvements

Future versions could introduce:

- RGB input
- HSL input
- HSL lightness control
- Color history
- Saved palettes
- Copy-to-clipboard functionality
- Complementary color generation
- Analogous color schemes
- Triadic color schemes
- Split-complementary palettes
- Random color generation
- Palette export
- Keyboard navigation
- URL-based color sharing
- Accessibility improvements
- PWA support

---

## License

This project is currently distributed without a specified open-source license.

If you intend to publish ChromaSphere as an open-source project, add an appropriate `LICENSE` file and update this section accordingly.

---

## Author

Developed as a standalone frontend project exploring interactive color selection, Canvas rendering, and browser-based color manipulation.
