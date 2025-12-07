# M4A to MP3 Converter

A simple macOS AppleScript application that converts M4A audio files to MP3 format.

## Features

- Batch convert multiple M4A files to MP3 in one go
- Two usage modes: file selection dialog or drag-and-drop
- Automatic fallback between multiple conversion tools
- Progress tracking with success/failure counts
- Native macOS integration

## Requirements

- macOS (tested with built-in tools)
- **Recommended**: [ffmpeg](https://ffmpeg.org/) for best conversion quality

## Installation

### Installing FFmpeg (Recommended)

For the best conversion results, install ffmpeg via Homebrew:

```bash
brew install ffmpeg
```

### Setting Up the Script

1. Save `convert_m4a_to_mp3.scpt` to your desired location
2. Double-click to run, or:
3. Open with Script Editor to modify/save as an application

To create a standalone app:
1. Open `convert_m4a_to_mp3.scpt` in **Script Editor**
2. Go to **File > Export**
3. Set **File Format** to "Application"
4. Save to your Applications folder or desired location

## Usage

### Method 1: File Selection

1. Double-click the script or application
2. A file picker dialog will appear
3. Select one or more M4A files to convert
4. Click "Choose"
5. The script will convert all selected files

### Method 2: Drag and Drop

1. Save the script as an Application (see Installation)
2. Drag M4A files directly onto the app icon
3. The conversion will start automatically

## How It Works

The script attempts conversion using multiple tools in order of preference:

1. **afconvert** - macOS built-in tool with AAC format
2. **ffmpeg** (Homebrew path: `/opt/homebrew/bin/ffmpeg`) - High-quality MP3 encoding
3. **ffmpeg** (alternate path: `/usr/local/bin/ffmpeg`) - Intel Mac Homebrew location

The output MP3 files are saved in the same directory as the source M4A files.

## Output

After conversion completes, you'll see a dialog showing:

- **Success case**: Number of files successfully converted
- **Partial failure case**:
  - Number of successful conversions
  - Number of failed conversions
  - Reminder to install ffmpeg if not present

## Troubleshooting

### "Conversion finished with some errors"

This usually means ffmpeg is not installed or not found in the expected paths. Install ffmpeg:

```bash
brew install ffmpeg
```

### Files not converting

- Ensure the files are actually M4A format
- Check that you have write permissions in the source directory
- Try installing ffmpeg for more reliable conversions

### Permission issues

If macOS blocks the script from running:
1. Go to **System Settings > Privacy & Security**
2. Allow the script to run under "Security"

## Technical Details

- **Conversion format**: MPEG Layer 3 (MP3)
- **Quality**: Variable based on the tool used (ffmpeg uses `-qscale:a 2` for high quality)
- **File naming**: Replaces `.m4a` extension with `.mp3`
- **Error handling**: Tracks both successful and failed conversions

## License

This is a utility script provided as-is for personal use.

## Contributing

Feel free to modify the script for your needs. The script is straightforward AppleScript and can be edited in Script Editor.

## Version

Current version handles both `.m4a` and `.M4A` file extensions (case-insensitive).
