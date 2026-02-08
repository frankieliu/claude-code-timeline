# Claude Code Timeline Viewer

A standalone HTML viewer for exploring Claude Code session files as an interactive timeline.

## Quick Start

### Launch the Viewer

**Option 1: Open directly (simplest)**
```bash
open index.html
```

**Option 2: Double-click**
Double-click `index.html` in Finder to open in your default browser.

**Option 3: Use a local server**
If you need CORS support for URL fetching:
```bash
python3 -m http.server 8000
```
Then open http://localhost:8000 in your browser.

### Load a Session File

1. **File Picker** - Click the drop zone and navigate to `~/.claude/projects/<project>/`
   - **Tip**: Press `Cmd+Shift+G` to paste the full path
2. **Drag & Drop** - Drop a `.jsonl` file onto the page
3. **Paste Content** - Switch to "Paste" tab and paste JSONL content directly
4. **Fetch from URL** - Switch to "URL" tab to load from a CORS-enabled URL

### Session Files Location

```
~/.claude/projects/<project-name>/<session-id>.jsonl
```

## Features

- **Interactive Timeline** - Navigate through all conversation events
- **Powerful Filtering** - Filter by type, content, role, or search terms
- **Sticky Controls** - Filter panel stays visible while scrolling
- **Time Display** - Toggle between local time and UTC
- **Extract Prompts** - Copy all user prompts from a session
- **Tool Analysis** - View all tool calls and results
- **Image Support** - View screenshots and images inline
- **Privacy First** - All processing happens locally in your browser

## Recommended Workflow

This workflow combines multiple tools for efficiently finding, analyzing, and resuming Claude Code sessions:

1. **Find the session file** - Use [Claude Code Viewer](../claude-code-viewer) to browse or search for `.jsonl` files
   - Use the info icon (ⓘ) to copy the full file path

2. **Load in Timeline Viewer** - Open this tool and load the session
   - Click the file picker and press `Cmd+Shift+G`
   - Paste the copied path to quickly navigate to the file

3. **Analyze the session** - Use filters to understand what happened
   - Example: Filter by "user + text" to see all user communications
   - Identify the point where you want to resume

4. **Navigate to project** - Open terminal and go to the project directory
   ```bash
   cd /path/to/your/project
   ```

5. **Resume Claude session** - Open Claude and select the session
   - Use `claude --resume` or `/resume` within Claude to select the session

6. **Rewind to specific point** - Use Claude's rewind feature
   - Use `/rewind` command or press `Esc` twice
   - Select the event number you identified in step 3

## Documentation

For detailed documentation, see the [docs directory](./docs/):

- **[Complete Documentation](./docs/README.md)** - Navigation, filtering, use cases, and troubleshooting
- **[Resuming Conversations](./docs/resuming-conversations.md)** - How to rewind and resume sessions
- **[Changelog](./docs/changelog.md)** - Version history and updates

## Source

This tool was originally taken from [Simon Willison's tools repository](https://github.com/simonw/tools/blob/main/claude-code-timeline.html) and has been enhanced with additional features.

## Privacy & Security

- No server communication - all processing is local
- No data storage - files processed in memory only
- No tracking or analytics
- Your session data never leaves your machine
