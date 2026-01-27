# Claude Code Timeline Viewer

A standalone HTML viewer for exploring Claude Code session files as an interactive timeline.

## Source

This tool was taken from [Simon Willison's tools repository](https://github.com/simonw/tools/blob/main/claude-code-timeline.html).

## How to Launch

### Option 1: Open directly in browser (simplest)
```bash
open index.html
```

### Option 2: Double-click
Double-click the `index.html` file in Finder to open it in your default browser.

### Option 3: Serve via HTTP server
If you need CORS support for URL fetching:
```bash
python3 -m http.server 8000
```
Then open http://localhost:8000 in your browser.

## How to Use

Once the viewer is open in your browser, you can load Claude Code session data in several ways:

1. **Drag and drop** - Drop a `.jsonl` file onto the dropzone
2. **File picker** - Click the dropzone to choose a file from your system
3. **Paste content** - Switch to the "Paste" tab and paste JSONL content directly
4. **Fetch from URL** - Switch to the "URL" tab to load from a CORS-enabled URL

### Finding Session Files

Claude Code session files are stored in `~/.claude/projects/`. Each project directory contains `.jsonl` files with the conversation history.

## Features

- Interactive timeline view of all events in a session
- Filter by event type, content type, and role
- Search through messages and tool usage
- View timestamps in local time or UTC
- Detailed view with formatted content and images
- Extract and copy all user prompts from a session
