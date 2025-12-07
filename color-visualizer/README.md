# Color Visualizer

A powerful macOS color visualization tool that generates beautiful color spectrum images from any color input.

## Features

- **Multiple Color Format Support**: HEX, RGB, CMYK, HSL, and HSB/HSV
- **Visual Spectrum Generation**: Generates comprehensive color spectrum visualizations including:
  - Main color swatch with detailed information
  - Hue spectrum (0° - 360°)
  - Lightness spectrum (0% - 100%)
  - Saturation spectrum (0% - 100%)
  - Color palette recommendations (Complementary, Analogous, Triadic, Split Complementary, Monochromatic)
- **Interactive HTML Version**: Generate interactive, clickable color pickers
- **Automatic Preview**: Opens generated images in Preview.app

## Requirements

- macOS (tested on macOS with Python 3)
- Python 3.x
- Pillow (PIL) library

## Installation

1. Install Python dependencies:
   ```bash
   pip install pillow
   # or
   python3 -m pip install pillow
   ```

2. Make Python scripts executable (optional):
   ```bash
   chmod +x generate_color_image.py
   chmod +x generate_color_spectrum.py
   chmod +x generate_interactive_spectrum.py
   ```

## Usage

### Using the AppleScript App

1. Open `ColorVisualizer.applescript` in Script Editor
2. Run the script (⌘R)
3. Enter a color in any supported format
4. View the generated spectrum in Preview.app

### Using Python Scripts Directly

**Generate detailed color image with palettes:**
```bash
./generate_color_image.py "#ffb6c1" output.png
```

**Generate simple spectrum visualization:**
```bash
./generate_color_spectrum.py "#ffb6c1" output.png
```

**Generate interactive HTML:**
```bash
./generate_interactive_spectrum.py "#ffb6c1" output.html
open output.html
```

## Supported Color Formats

| Format | Example | Description |
|--------|---------|-------------|
| HEX | `#ffb6c1` or `ffb6c1` | Hexadecimal color code |
| RGB | `rgb(255, 182, 193)` or `255,182,193` | Red, Green, Blue values (0-255) |
| CMYK | `cmyk(0, 29, 24, 0)` | Cyan, Magenta, Yellow, Key (0-100) |
| HSL | `hsl(351, 100, 86)` | Hue (0-360°), Saturation (0-100%), Lightness (0-100%) |
| HSB/HSV | `hsb(351, 29, 100)` | Hue (0-360°), Saturation (0-100%), Brightness (0-100%) |

## Files

- `ColorVisualizer.applescript` - Main AppleScript application with color parsing and UI
- `generate_color_image.py` - Generates detailed spectrum with palette recommendations
- `generate_color_spectrum.py` - Generates simple spectrum visualization with hue, lightness, and saturation bars
- `generate_interactive_spectrum.py` - Creates interactive HTML color picker with clickable colors

## Example Outputs

The Color Visualizer generates:

1. **Main Color Information**: Displays the input color with HEX, RGB, and HSL values
2. **Hue Spectrum**: Shows how the color varies across the hue wheel
3. **Lightness Spectrum**: Demonstrates the color at different brightness levels
4. **Saturation Spectrum**: Shows the color from grayscale to fully saturated
5. **Color Palettes**: Suggests harmonious color combinations based on color theory

## Building as macOS App

To create a standalone macOS application:

1. Open `ColorVisualizer.applescript` in Script Editor
2. Go to File → Export
3. Choose File Format: Application
4. Save the app
5. Copy the Python scripts to the app's Resources folder:
   ```bash
   cp generate_color_image.py "ColorVisualizer.app/Contents/Resources/"
   ```

## Technical Details

### Color Conversion

The AppleScript handles conversion between different color formats:
- HEX to RGB conversion using hexadecimal parsing
- CMYK to RGB using standard color space conversion formulas
- HSL to RGB using hue calculation algorithms
- HSB/HSV to RGB using brightness/value calculations

### Python Scripts

All three Python scripts use the Pillow (PIL) library for image generation and include:
- Custom color space conversion functions
- Dynamic font loading with fallbacks
- Color palette generation based on color theory
- Interactive HTML with JavaScript for the web version

## License

MIT License - feel free to use and modify as needed.
