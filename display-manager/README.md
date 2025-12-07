# Smart Display Resolution Manager

An AppleScript that automatically adjusts your MacBook's built-in display resolution based on whether an external monitor is connected.

## Overview

This script intelligently manages display resolutions by:
- Detecting the number of connected displays
- Automatically switching between optimized resolutions
- Configuring display positioning when using multiple monitors

## Features

- **Automatic Resolution Switching**
  - **Single Display Mode**: Sets built-in display to 1800x1125 (preferred resolution for maximum screen real estate)
  - **Dual Display Mode**: Sets built-in display to 1512x982 (default resolution for better compatibility)

- **Multi-Monitor Support**: Automatically configures external monitor positioning
- **Error Handling**: Provides notifications and logging for troubleshooting
- **Non-Destructive**: Only adjusts display settings, no system modifications

## Prerequisites

### displayplacer

This script requires the `displayplacer` command-line tool:

```bash
brew install displayplacer
```

Or install via the [displayplacer GitHub repository](https://github.com/jakehilborn/displayplacer).

## Installation

1. Clone or download this repository
2. Ensure `displayplacer` is installed (see Prerequisites)
3. Open `display-manager.scpt` in Script Editor
4. Save as an Application or use directly

## Usage

### Run Manually

```bash
osascript display-manager.scpt
```

Or double-click the script in Finder (if saved as an Application).

### Automate with Launch Agent

To run automatically when displays change, create a Launch Agent or use a tool like [Hammerspoon](https://www.hammerspoon.org/) or [BetterTouchTool](https://folivora.ai/).

### Example: Run on Login

1. Open Script Editor
2. Export the script as an Application
3. Add to System Preferences > Users & Groups > Login Items

## How It Works

1. **Display Detection**: Uses `displayplacer list` to enumerate connected displays
2. **Built-in Display Identification**: Parses output to find the built-in display's persistent screen ID
3. **Resolution Selection**:
   - If 2+ displays detected → Apply 1512x982 to built-in display
   - If only 1 display → Apply 1800x1125 to built-in display
4. **Configuration**: Executes `displayplacer` with appropriate parameters
5. **Notification**: Shows macOS notification confirming the change

## Display Configurations

### Single Display Mode (1800x1125)
- **Resolution**: 1800 x 1125
- **Refresh Rate**: 120 Hz
- **Color Depth**: 8-bit
- **Scaling**: On
- **Origin**: (0, 0)

### Dual Display Mode (1512x982)
**Built-in Display:**
- **Resolution**: 1512 x 982
- **Refresh Rate**: 120 Hz
- **Origin**: (-1512, 0) - positioned to the left of external

**External Display:**
- **Resolution**: 1920 x 1080
- **Refresh Rate**: 60 Hz
- **Origin**: (0, 0) - primary display

## Customization

To modify resolutions, edit the `displayplacer` commands in the script:

```applescript
-- Single display mode
set shellCmd to "displayplacer \"id:" & builtInID & " res:1800x1125 hz:120 color_depth:8 enabled:true scaling:on origin:(0,0) degree:0\""

-- Dual display mode (built-in)
"id:" & builtInID & " res:1512x982 hz:120 color_depth:8 enabled:true scaling:on origin:(-1512,0) degree:0"
```

Find available resolutions for your display:

```bash
displayplacer list
```

## Troubleshooting

### Script Fails with "Could not find built-in display"

Check that `displayplacer` can detect your display:

```bash
displayplacer list | grep "built in"
```

### Wrong Resolution Applied

1. Run `displayplacer list` to see available resolutions
2. Update the script with your preferred resolution values
3. Ensure the resolution is supported by your display

### No Notification Shown

Check System Preferences > Notifications to ensure Script Editor or your exported app has notification permissions.

## Logs

The script outputs to the system log. View logs using:

```bash
log show --predicate 'process == "osascript"' --last 5m
```

Or check Console.app and filter for "display" or "displayplacer".

## Compatibility

- **macOS**: 10.14 (Mojave) or later
- **Displays**: MacBook Pro/Air with built-in Retina display
- **External Monitors**: Any displayplacer-compatible external display

## License

This script is provided as-is for personal use.

## Credits

Built with:
- [displayplacer](https://github.com/jakehilborn/displayplacer) by Jake Hilborn
- AppleScript
