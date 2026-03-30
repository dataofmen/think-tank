---
url: https://x.com/NickSpisak_/status/2037192071254048947
crawled: 2026-03-30
author: Nick Spisak (@NickSpisak_)
type: twitter-thread
---

# Claude Code Channels + Mac Mini 24/7 AI Assistant Setup

## Thread (2026-03-26)

Tweet ID: 2037192071254048947

## Key Quotes

> "Claude Code Channels has no message queue. If Claude's session isn't running when you send a Telegram message, that message is gone. Not saved for later. Not waiting in line. Just lost."

> "The path trick nobody mentions: Claude Code tracks your projects by the exact folder path on your computer. If your laptop uses /Users/nick/Projects/ but your Mini uses /Users/admin/Projects/, Claude gets confused. The fix: use the same username on both machines."

> "Why LaunchAgent and not a cron job: Cron runs in a stripped-down environment that can't access your login credentials. Claude Code needs your authentication to work, and LaunchAgents run inside your user session where those credentials are available."

## Core Setup

### Components
- **Claude Code Channels**: Official Anthropic feature for Telegram/Discord/iMessage remote access
- **Mac Mini M4**: Always-on hardware (no monitor needed)
- **SyncThing**: Free P2P file synchronization between computers
- **LaunchAgent**: macOS native auto-restart mechanism

### What to Sync
✅ Sync:
- ~/.claude/skills
- ~/.claude/commands
- ~/.claude/settings.json
- Knowledge base files
- MCP configs

❌ Don't Sync:
- settings.local.json (machine-specific paths)
- history.jsonl (session logs)
- projects/ (absolute paths cause conflicts)

## Technical Details

### SyncThing Configuration

SyncThing is a free, open-source P2P file sync tool (since 2013). No cloud required. Works for dotfiles and config directories.

**Key insight**: Use the same username on both machines to avoid path conflicts with Claude Code's project tracking.

### LaunchAgent Script

```bash
#!/bin/zsh
# ~/.claude/scripts/claude-channels-restart.sh
tmux kill-session -t claude-channels 2>/dev/null
sleep 2
tmux new-session -d -s claude-channels -c ~/Projects
tmux send-keys -t claude-channels "unset CLAUDECODE" Enter
tmux send-keys -t claude-channels "claude --channels plugin:telegram@claude-plugins-official" Enter
sleep 20
tmux send-keys -t claude-channels "Resume monitoring. Check channels for any messages." Enter
```

### LaunchAgent Plist

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
    <key>Label</key>
    <string>com.claude.channels</string>
    <key>ProgramArguments</key>
    <array>
        <string>/bin/zsh</string>
        <string>-c</string>
        <string>~/.claude/scripts/claude-channels-restart.sh</string>
    </array>
    <key>RunAtLoad</key>
    <true/>
    <key>StartCalendarInterval</key>
    <dict>
        <key>Hour</key>
        <integer>4</integer>
        <key>Minute</key>
        <integer>0</integer>
    </dict>
    <key>StandardOutPath</key>
    <string>/tmp/claude-channels.log</string>
    <key>StandardErrorPath</key>
    <string>/tmp/claude-channels.log</string>
</dict>
</plist>
```

## Limitations

- **No message queue**: Offline = messages lost (critical limitation)
- **Credential dependency**: Requires user session authentication (not system-level)
- **Path sensitivity**: Project paths must match across synced machines

## Advantages over Alternatives

- **vs Cloud VMs**: No ongoing cost, local file access, zero network latency
- **vs OpenClaw**: Official Anthropic feature, no third-party dependency
- **vs Git for dotfiles**: Real-time sync, no manual commits