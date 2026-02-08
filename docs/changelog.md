# Changelog

All notable changes to the Claude Code Timeline Viewer project.

## [Unreleased]

### Added

#### File Path Navigation Improvements
- **Cmd+Shift+G Tip**: Added helpful tip to the drop zone explaining that users can press `Cmd+Shift+G` in the macOS file picker to paste a file path and navigate directly to it
  - This addresses the browser security limitation that prevents programmatic navigation to arbitrary file paths
  - Provides a clear workflow: click drop zone → file picker opens → press Cmd+Shift+G → paste path → navigate

#### UI/UX Enhancements
- **Sticky Filters Panel**: The filters panel now stays visible at the top of the viewport while scrolling
  - `position: sticky` with `top: 0` keeps controls accessible anywhere in the timeline
  - `z-index: 10` ensures it stays above content
  - Solid background prevents content from showing through

- **Detail Panel Positioning**: Adjusted the detail panel's sticky position to prevent overlap with the sticky filters panel
  - Changed `top: 16px` to `top: 90px` on desktop viewports (≥1060px)
  - Adjusted `max-height` calculation from `calc(100vh - 32px)` to `calc(100vh - 100px)`
  - Ensures "Copy JSON" and "Copy raw line" buttons remain fully visible while scrolling

- **Integrated Controls**: Moved "Show prompts" button into the filters panel
  - Consolidated all filtering and viewing controls into a single, organized section
  - Removed standalone controls section for cleaner layout
  - All controls now in one location: Timezone, Search, Type, Content Type, Role, Hide thinking, Clear, and Show prompts

### Removed
- **File Path Tab**: Removed the experimental "File Path" tab that attempted to provide file path input
  - Browser security restrictions prevent JavaScript from accessing arbitrary file paths
  - The tab added complexity without solving the core limitation
  - Replaced with simpler, more effective Cmd+Shift+G tip in the drop zone

### Technical Details

#### CSS Changes
```css
/* Added sticky positioning to filters panel */
.filters-panel {
  position: sticky;
  top: 0;
  z-index: 10;
  background: var(--panel);
}

/* Adjusted detail panel to accommodate sticky filters */
@media (min-width: 1060px) {
  .detail {
    top: 90px;  /* Previously 16px */
    max-height: calc(100vh - 100px);  /* Previously calc(100vh - 32px) */
  }
}
```

#### HTML Structure Changes
- Consolidated filters panel to include Show prompts button
- Added Cmd+Shift+G tip to drop zone with visual formatting
- Removed File Path tab and associated input elements

#### JavaScript Changes
- Removed File Path tab event handlers (file path input, browse button, load path button, copy directory button)
- No new JavaScript functionality added (all changes were CSS/HTML)

### Browser Compatibility
- Sticky positioning supported in all modern browsers
- macOS Cmd+Shift+G navigation works in all standard file pickers
- No new JavaScript APIs used that would affect compatibility

### User Experience Improvements
- **Faster Access to Controls**: Filters always visible reduces scrolling and improves workflow efficiency
- **Clearer File Navigation**: Direct instruction about Cmd+Shift+G is more helpful than attempting programmatic workarounds
- **Better Visual Hierarchy**: Consolidated controls provide clearer mental model of available actions
- **No Overlap Issues**: Detail panel properly positioned prevents content from being hidden

## [1.0.0] - Initial Release

### Features
- Timeline visualization of Claude Code session JSONL files
- Multiple input methods: file picker, drag-and-drop, paste, URL fetch
- Filtering by type, content type, role, and search query
- Timezone toggle (Local/UTC)
- Event selection with detailed view
- JSON export (formatted and raw)
- Image viewing for screenshots
- Pretty-formatted view for messages and tool calls
- User prompts extraction
- Dark/light mode support
- Responsive layout
- Keyboard navigation
- Markdown rendering for messages
- Accessibility features (ARIA labels, keyboard support)

### Technical Stack
- Single HTML file with embedded CSS and JavaScript
- No build process required
- External dependencies:
  - DOMPurify (v3.2.3) - XSS protection
  - markdown-it (v4.4.0) - Markdown rendering
- Vanilla JavaScript (ES6+)
- CSS custom properties for theming
- Progressive enhancement approach

## Future Considerations

### Potential Enhancements
- Export timeline as Markdown document
- Jump to event by number (input field)
- Bookmarking/starring important events
- Diff view for file changes
- Timeline visualization (visual timeline chart)
- Session comparison (side-by-side view)
- Export filtered events
- Session statistics dashboard
- Tool usage analytics
- Performance metrics visualization

### Known Limitations
- Browser file access limited by security policies (expected)
- URL fetch requires CORS-enabled endpoints
- Large files (>10k events) may impact performance
- No server-side processing or storage
- No authentication or access control

### Browser Support
- Modern browsers with ES6+ support
- Tested on Chrome, Safari, Firefox, Edge
- Mobile responsive but optimized for desktop use
