# ClipLogger — Clipboard Monitoring Tool (Windows)

## Summary (XYZ)
- **Accomplished clipboard visibility** as measured by **timestamped logs of text and file operations** by **monitoring clipboard changes and filesystem events.**
- **Accomplished storage-type awareness** as measured by **correct categorization (internal/external/network/optical)** by **inspecting drive metadata and correlating with clipboard/file activity.**

## Tech
Python · pywin32 · watchdog · psutil · wmi

## How it works (high level)
- Watches clipboard for changes
- Detects file paste operations across drives
- Uses system info to classify storage types
- Logs events with timestamps

## Running locally
- Requires Windows + Python 3.8+
- Run with Administrator privileges for filesystem monitoring

## Screenshots
- `assets/screenshots/cliplogger/`
