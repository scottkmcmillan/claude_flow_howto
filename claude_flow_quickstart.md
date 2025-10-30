# Claude Flow Quick Start


# Resume a session

After a crash or taking a break

```bash
npx @anthropic-ai/claude-code --dangerously-skip-permissions
claude -c --dangerously-skip-permissions
```
it will look at the memory and determine where it left off and then spawn new agents to start where it left off.

with input line, explain what happended and to continue where you were at (e.g. continue spawning the swarm, continue with the hive mind, etc)


# Get help and see available commands
claude-flow --help

# Quick AI coordination (recommended for most tasks)
claude-flow swarm "build me a REST API" --claude

# Launch the full hive-mind system (for complex projects)
claude-flow hive-mind wizard
claude-flow hive-mind spawn "build enterprise system" --claude

# Test hive-mind coordination
claude-flow hive-mind test --agents 5 --coordination-test

# Verify system status
claude-flow hive status
claude-flow mcp tools list
claude-flow sparc modes