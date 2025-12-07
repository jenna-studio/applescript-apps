# Custom Color Picker

A macOS AppleScript application that provides an enhanced color picker with multi-format color output.

## Overview

This tool opens the native macOS Color Picker and converts your selected color into multiple popular color formats, making it easy to use colors across different development and design contexts.

## Features

### Supported Color Formats

- **Hex** - `#C5EFFE`
- **RGB** - `rgb(197, 239, 254)`
- **RGBA** - `rgba(197, 239, 254, 1.0)`
- **HSL** - `hsl(196, 97%, 88%)`
- **HSV** - `hsv(196, 22%, 100%)`
- **CMYK** - `cmyk(22%, 6%, 0%, 0%)`
- **Raw RGB** - `197, 239, 254`

### Copy Options

After selecting a color, you can:
- **Copy Hex** - Copy just the hex value
- **Copy RGB** - Copy just the RGB value
- **Copy All** - Copy all color formats at once

## Files

- `custom-color-picker.scpt` - Standalone AppleScript file
- `Custom Color Picker.app` - Packaged macOS application

## Usage

### Running the Application

1. Double-click `Custom Color Picker.app` to launch
2. The macOS Color Picker will open
3. Select your desired color
4. Click "Select" to confirm
5. A dialog will display all color format conversions
6. Choose your preferred copy option

### Running the Script

```bash
osascript custom-color-picker.scpt
```

## Technical Details

### Color Conversion Functions

The script includes helper functions for accurate color space conversions:

- `rgbToHSL(r, g, b)` - Converts RGB (0-1) to HSL format
- `rgbToHSV(r, g, b)` - Converts RGB (0-1) to HSV format
- `rgbToCMYK(r, g, b)` - Converts RGB (0-1) to CMYK format
- `toHex(decValue)` - Converts decimal (0-255) to hexadecimal

### Color Space Handling

- AppleScript's native color picker returns RGB values in the 0-65535 range
- Values are normalized to 0-255 for standard RGB output
- Values are normalized to 0-1 for HSL, HSV, and CMYK calculations
- All percentage values are rounded to whole numbers for readability

## Requirements

- macOS (any recent version with AppleScript support)
- No additional dependencies required

## Building from Source

To create your own .app bundle:

1. Open Script Editor (Applications > Utilities > Script Editor)
2. Open `custom-color-picker.scpt`
3. File > Export
4. Set File Format to "Application"
5. Choose a save location

## Use Cases

- Web development (CSS colors)
- Graphic design (color values for design tools)
- Documentation (color specifications)
- Digital art (color palette creation)
- UI/UX design (design system colors)

## License

This project is open source and available for personal and commercial use.

## Contributing

Feel free to fork, modify, and enhance this color picker tool. Potential improvements could include:
- Additional color formats (Lab, XYZ, etc.)
- Color palette generation
- Recent colors history
- Custom output format templates
- Integration with design tools
