# Setting Up Claude Flow in GitHub Codespaces

## Overview

Claude Flow is a revolutionary AI orchestration platform that coordinates multiple Claude Code instances to work together on complex tasks. This guide will help you set up Claude Flow in GitHub Codespaces, providing a consistent development environment in the cloud.

## Prerequisites

- GitHub account with Codespaces access
- Basic familiarity with Git and GitHub

## Quick Setup Guide

### 1. Create a New Repository (or Use an Existing One)

1. Create a new repository on GitHub or use an existing one
2. Open the repository in GitHub Codespaces by clicking the "Code" button and selecting "Open with Codespaces"

### 2. Install Required Packages

GitHub Codespaces comes with Node.js and npm pre-installed. You have two options for installing Claude Flow:

#### Option A: Global Installation (Recommended for Long-Term Use)

```bash
# Install Claude Code globally
npm install -g @anthropic-ai/claude-code

# Install Claude Flow Alpha version globally
npm install -g claude-flow@alpha

# Verify installations
node --version    # Should be 18+ (LTS)
npm --version     # Should be 9+
claude --version  # Should show Claude Code version
claude-flow --version  # Should show v2.0.0-alpha.53+
```

#### Option B: Local Usage with npx (No Installation Required)

```bash
# Run Claude Code without installation
npx @anthropic-ai/claude-code --dangerously-skip-permissions

# Run Claude Flow commands directly without installation
npx claude-flow@alpha --help
npx claude-flow@alpha init --force
```

#### Difference Between Global Installation and npx

- **Global Installation** (`npm install -g`):
  - Installs the packages permanently on your system
  - Commands are available directly (e.g., `claude-flow` instead of `npx claude-flow@alpha`)
  - Better for frequent use and persistent projects
  - Requires updating manually when new versions are released

- **npx Usage**:
  - Runs the latest version without installing permanently
  - Perfect for trying out Claude Flow without modifying your system
  - Always uses the latest version from npm registry
  - Slightly slower startup time as it downloads the package each time
  - Ideal for temporary Codespaces or quick experiments

## Authentication Workflow

### 1. Authenticate Claude Code

```bash
# Start Claude and authenticate
claude --dangerously-skip-permissions
```

- Complete the login process with your Anthropic account
- Choose subscription (default) or API key option
- Exit Claude after authentication completes

> **Note:** Authentication persists in secure storage after exit in `~/.claude/` and `~/.config/claude-code/auth.json`

### 2. Initialize Claude Flow

```bash
# Basic initialization with SPARC methodology
claude-flow init --sparc

# OR initialize with full alpha features (recommended for Codespaces)
claude-flow init --force --hive-mind --neural-enhanced

# Configure Claude Code integration with all 87 MCP tools
claude-flow mcp setup --auto-permissions --87-tools
```

This creates:
- `.claude/` directory with configuration
- `CLAUDE.md` (project instructions)
- `.roomodes` (pre-configured SPARC modes)
- MCP server configuration with advanced tools

## Using Claude Flow

### Basic Commands

```bash
# Get help and see available commands
claude-flow --help

# Quick AI coordination (recommended for most tasks)
claude-flow swarm "build me a REST API"

# Launch the full hive-mind system (for complex projects)
claude-flow hive-mind wizard
claude-flow hive-mind spawn "build enterprise system" --claude

# Test hive-mind coordination
claude-flow hive-mind test --agents 5 --coordination-test

# Verify system status
claude-flow hive status
claude-flow mcp tools list
claude-flow sparc modes
```

### Swarm vs Hive-Mind

- **Swarm**: Use for most tasks. Quick, ephemeral coordination.
- **Hive-Mind**: Use for complex projects requiring persistent sessions and multi-agent coordination.

## Troubleshooting

### Common Issues

1. **Authentication Problems**:
   - Ensure you've authenticated Claude Code first
   - Check for auth files in `~/.claude/` and `~/.config/claude-code/auth.json`

2. **Installation Issues**:
   - Verify Node.js version is 18+
   - Try reinstalling: `npm install -g claude-flow@alpha`
   - Clear npm cache if needed: `npm cache clean --force`

3. **Resource Constraints**:
   - Increase GitHub Codespaces resources if needed
   - Use `--memory-efficient` flag with Claude Flow commands

4. **Windows-Specific Issues**:
   - If you encounter SQLite errors, Claude Flow will automatically use in-memory storage
   - For persistent storage options on Windows, see the [Windows guide](https://github.com/ruvnet/claude-flow/wiki/Windows-Installation)

## Important Notes

- Some GitHub integration commands documented in Claude Flow may not be fully implemented in the alpha version
- Use general swarm commands and direct Claude Flow interactions instead of specialized GitHub commands if you encounter "Unknown GitHub mode" errors
- The alpha version is under active development; features may change

## Additional Resources

- [Claude Flow GitHub Repository](https://github.com/ruvnet/claude-flow)
- [Claude Flow Wiki](https://github.com/ruvnet/claude-flow/wiki)
- [Installation Guide](https://github.com/ruvnet/claude-flow/wiki/Installation-Guide)
- [Quick Start Guide](https://github.com/ruvnet/claude-flow/wiki/Quick-Start)
