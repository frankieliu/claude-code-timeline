# Resuming Conversations from JSONL Files

This guide explains how to pick up a conversation at a particular point using Claude Code session files (`.jsonl`).

## Understanding Session Files

Claude Code stores conversation history in JSONL (JSON Lines) files located at:
```
~/.claude/projects/<project-name>/<session-id>.jsonl
```

Each line in the file represents an event in the conversation timeline.

## Methods to Resume Conversations

### 1. **Using /rewind Command (Recommended)**

The easiest way to resume from a specific point in your current session:

1. **Open the timeline viewer** and load your session file
2. **Find the point** where you want to rewind to
3. **Note the event number** (shown as `#123` in the timeline)
4. **In Claude Code CLI**, press `Esc` twice (or type `/rewind`)
5. **Specify the event number** to rewind to

**Quick shortcut:** Press `Esc` `Esc` to trigger the rewind command

This will:
- Rewind the conversation to that specific point
- Discard all events after that point
- Allow you to continue from there with a fresh direction

### 2. **Extract User Prompts from Timeline Viewer**

To copy conversation context for a new session:

1. **Load the JSONL file** in the timeline viewer
2. **Filter the timeline:**
   - Set **Type** to `user`
   - Set **Content Type** to `text`
   - Or set **Role** to `user`
3. **Click "Show prompts"** button in the filters panel
4. **Review** all user messages in chronological order
5. **Copy** the prompts you want to provide as context
6. **Start a new Claude Code session** and paste the context

This is useful when you want to:
- Share context with someone else
- Start a fresh session with specific background
- Extract only certain parts of a conversation

### 3. **Copy Specific Event Context**

For more granular control:

1. **Navigate to the event** where you want to resume in the timeline
2. **Click on the event** to view details
3. **Use action buttons:**
   - **Copy JSON** - Full structured event data
   - **Copy raw line** - Raw JSONL line
4. **Extract the message content** from the JSON
5. **Provide as context** in a new conversation

### 4. **Continue Active Session**

If your Claude Code session is still running:
- Simply continue typing in the same terminal
- The session file is updated in real-time
- No need to manually resume or reload

## Using the Timeline Viewer Effectively

### Navigation Tips

- **Sticky Filters Panel**: The filters panel stays visible while scrolling, making it easy to adjust filters anywhere in the timeline
- **Search**: Use the search box to find specific messages, tool names, or content
- **Keyboard Navigation**: Use arrow keys to move between events when focused on the timeline
- **Time Delta**: Each event shows the time elapsed since the previous event

### Filtering Conversations

- **Type Filter**: `user`, `assistant`, or `file-history-snapshot`
- **Content Type Filter**: `text`, `tool_use`, `tool_result`, `thinking`, `image`
- **Role Filter**: `user` or `assistant`
- **Hide Thinking**: Toggle to hide verbose thinking blocks

### Finding Key Moments

1. Use **Search** to find specific topics or commands
2. Look for **time deltas** to identify natural break points
3. Filter by **tool_use** to see what actions were taken
4. Filter by **user** messages to see conversation checkpoints

## Best Practices

### When to Use /rewind

- You want to try a different approach from a specific point
- An error occurred and you want to go back before it
- The conversation went in the wrong direction
- You want to explore alternative solutions from a checkpoint

### When to Extract Prompts

- Sharing conversation context with a team
- Starting a fresh session with clean state
- Documenting requirements or decisions
- Creating examples or templates

### When to Start Fresh

- The conversation has become too long and unfocused
- You want to simplify context for better performance
- You're switching to a different but related task
- You want to test Claude's response without prior context

## Tips for Effective Session Management

1. **Bookmark Important Events**: Note down event numbers (`#123`) for key moments
2. **Use Descriptive Messages**: Clear user messages make it easier to find resume points
3. **Regular Checkpoints**: Periodically summarize progress in your messages
4. **Clean Rewinding**: Use `/rewind` to keep sessions focused and performant
5. **Export Key Decisions**: Use "Show prompts" to document important conversations

## Example Workflow

```bash
# Working on a feature
$ claude

> Implement user authentication...
# [Claude helps implement auth]

> Add OAuth support...
# [Claude adds OAuth, but you realize you want JWT instead]

# Press Esc Esc to trigger /rewind
# Specify event number before OAuth work started
# Continue from there:

> Actually, let's add JWT support instead...
# [Claude implements JWT from the checkpoint]
```

## Troubleshooting

**Q: Can't find the session file?**
- Check `~/.claude/projects/` for your project
- Session files are named with UUID format: `<uuid>.jsonl`
- Use the most recently modified file if unsure

**Q: /rewind not working?**
- Ensure you're in an active Claude Code session
- Try typing `/rewind` explicitly instead of using Esc-Esc
- Check Claude Code version supports this feature

**Q: Show prompts button is disabled?**
- Load a JSONL file first using the file picker or drag-and-drop
- Ensure the file has valid user messages
- Check the file format is correct JSONL

**Q: Timeline shows too many events?**
- Use filters to narrow down the view
- Enable "Hide thinking" to reduce verbose blocks
- Use search to find specific content

## Related Features

- **Timezone Toggle**: Switch between local time and UTC for timestamps
- **Copy Actions**: Copy JSON or raw lines for external processing
- **Pretty View**: Formatted, readable view of messages and tool calls
- **Image Support**: View screenshots and images in the timeline
