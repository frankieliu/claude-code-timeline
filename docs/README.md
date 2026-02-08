# Claude Code Timeline Viewer Documentation

Welcome to the documentation for the Claude Code Timeline Viewer.

## Quick Links

- **[Resuming Conversations](./resuming-conversations.md)** - Learn how to pick up conversations at specific points using `/rewind` and other methods
- **[Changelog](./changelog.md)** - Track all changes and improvements to the project

## Overview

The Claude Code Timeline Viewer is a web-based tool for exploring and analyzing Claude Code session files (`.jsonl` format). It provides an interactive timeline interface for navigating conversation history, filtering events, and extracting context.

## Getting Started

### Opening Files

Three ways to load a session file:

1. **File Picker**
   - Click the drop zone "Drop a .jsonl file here"
   - **Tip**: Press `Cmd+Shift+G` in the file picker to paste a full path
   - Navigate to: `~/.claude/projects/<project-name>/<session-id>.jsonl`

2. **Drag and Drop**
   - Drag a `.jsonl` file from Finder onto the drop zone
   - Quick and intuitive for frequent use

3. **Paste Content**
   - Switch to "Paste" tab
   - Paste JSONL content directly
   - Click "Render pasted content"

4. **Fetch from URL**
   - Switch to "URL" tab
   - Enter a CORS-enabled URL to a `.jsonl` file
   - Click "Fetch and render"

### Navigation

- **Timeline View**: Scrollable list of all events in chronological order
- **Sticky Filters**: Control panel stays visible while scrolling
- **Event Selection**: Click any event to view details
- **Keyboard Navigation**: Use arrow keys to move between events

### Filtering

The filters panel provides multiple ways to narrow down events:

- **Search**: Text search across messages, tool names, paths, etc.
- **Type**: Filter by event type (user, assistant, file-history-snapshot)
- **Content Type**: Filter by content (text, tool_use, tool_result, thinking, image)
- **Role**: Filter by role (user, assistant)
- **Hide Thinking**: Toggle to hide verbose thinking blocks
- **Clear**: Reset all filters

### Key Features

- **Timezone Toggle**: Switch between local time and UTC
- **Event Details**: See formatted messages, tool calls, and results
- **Copy Actions**: Copy event JSON or raw JSONL line
- **Show Prompts**: Extract all user prompts from the session
- **Image Viewer**: View screenshots and images inline
- **Time Deltas**: See elapsed time between events

## Common Use Cases

### Finding Specific Events
1. Use the **Search** box to find keywords
2. Filter by **Type** or **Content Type** to narrow results
3. Look at **time deltas** to find natural break points
4. Click events to view full details

### Extracting User Prompts
1. Click **"Show prompts"** in the filters panel
2. Review all user messages in chronological order
3. Copy the prompts you need
4. Use as context in a new session

### Analyzing Tool Usage
1. Filter **Content Type** to `tool_use`
2. Review what tools were called
3. Click events to see tool inputs and outputs
4. Identify patterns or issues

### Reviewing Conversation Flow
1. Filter by **Role** to see user or assistant messages
2. Hide thinking blocks for cleaner view
3. Navigate with arrow keys for quick scanning
4. Note event numbers for key moments

## Tips and Tricks

### Performance
- Use filters to reduce visible events for smoother scrolling
- Enable "Hide thinking" for faster rendering
- Search is case-insensitive and searches all fields

### Workflow Integration
- Bookmark event numbers (`#123`) for important moments
- Use "Show prompts" to create documentation
- Export JSON for external processing
- Take notes of key event numbers before using `/rewind`

### Keyboard Shortcuts
- **Arrow Up/Down**: Navigate between events (when timeline focused)
- **Esc**: Close image viewer or prompts modal
- **Cmd+Shift+G**: In file picker, paste a path to navigate (macOS)

## File Format

Claude Code session files use JSONL format (JSON Lines):
- Each line is a complete JSON object
- One event per line
- Chronologically ordered
- Real-time updates during active sessions

## Session Files Location

Default location:
```
~/.claude/projects/<project-name>/<session-id>.jsonl
```

Project-specific sessions are organized by directory name.

## Privacy and Security

- **No server communication**: All processing happens in your browser
- **No data storage**: Files are processed in memory only
- **No tracking**: No analytics or external requests (except optional URL fetch)
- **Local only**: Your session data never leaves your machine

## Browser Requirements

- Modern browser with ES6+ support (Chrome, Safari, Firefox, Edge)
- JavaScript enabled
- Local file access (for file picker and drag-and-drop)
- ~100MB free memory for large session files

## Troubleshooting

**File won't load?**
- Check that it's a valid JSONL file
- Ensure each line is valid JSON
- Try pasting content in "Paste" tab to see specific errors

**Filters panel covering content?**
- Detail panel should automatically adjust position
- Try zooming out or expanding window

**Show prompts disabled?**
- Load a file first
- Ensure the file contains user messages

**Can't find session file?**
- Check `~/.claude/projects/` directory
- Look for recently modified `.jsonl` files
- Session IDs are UUIDs (e.g., `abc123-def456-...`)

## Contributing

Found a bug or have a feature request? Please check the project repository for contribution guidelines.

## License

See the main project README for license information.
