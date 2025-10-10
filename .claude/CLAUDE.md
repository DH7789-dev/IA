# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## User Configuration Directory

This is the Claude Code configuration directory (`~/.claude`) containing user settings, project data, custom commands, and security configurations.

## Security System

The system includes a comprehensive security validation hook:

- **Command Validation**: `/Users/david/.claude/scripts/validate-command.js` - A Bun-based security script that validates commands before execution
- **Protected Operations**: Blocks dangerous commands like `rm -rf /`, system modifications, privilege escalation, network tools, and malicious patterns
- **Security Logging**: Events are logged to `/Users/melvynx/.claude/security.log` for audit trails
- **Fail-Safe Design**: Script blocks execution on any validation errors or script failures

The security system is automatically triggered by the PreToolUse hook configured in `settings.json`.

## Custom Commands

Three workflow commands are available in the `/commands` directory:

### `/run-task` - Complete Feature Implementation
Workflow for implementing features from requirements:
1. Analyze file paths or GitHub issues (using `gh cli`)
2. Create implementation plan
3. Execute updates with TypeScript validation
4. Auto-commit changes
5. Create pull request

### `/fix-pr-comments` - PR Comment Resolution
Workflow for addressing pull request feedback:
1. Fetch unresolved comments using `gh cli`
2. Plan required modifications
3. Update files accordingly
4. Commit and push changes

### `/explore-and-plan` - EPCT Development Workflow
Structured approach using parallel subagents:
1. **Explore**: Find and read relevant files
2. **Plan**: Create detailed implementation plan with web research if needed
3. **Code**: Implement following existing patterns and run autoformatting
4. **Test**: Execute tests and verify functionality
5. Write up work as PR description

## Status Line

Custom status line script (`statusline-ccusage.sh`) displays:
- Git branch with pending changes (+added/-deleted lines)
- Current directory name
- Model information
- Session costs and daily usage (if `ccusage` tool available)
- Active block costs and time remaining
- Token usage for current session

## Hooks and Audio Feedback

- **Stop Hook**: Plays completion sound (`finish.mp3`) when tasks complete
- **Notification Hook**: Plays notification sound (`need-human.mp3`) for user interaction
- **Pre-tool Validation**: All Bash commands are validated by the security script

## Project Data Structure

- `projects/`: Contains conversation history in JSONL format organized by directory paths
- `todos/`: Agent-specific todo lists for task tracking
- `shell-snapshots/`: Shell state snapshots for session management
- `statsig/`: Analytics and feature flagging data

## Permitted Commands

The system allows specific command patterns without additional validation:
- `git *` - All Git operations
- `npm run *` - NPM script execution
- `pnpm *` - PNPM package manager
- `gh *` - GitHub CLI operations
- Standard file operations (`cd`, `ls`, `node`)