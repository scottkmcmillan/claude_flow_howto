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

#### Option A: Local Usage with npx (No Installation Required - recommended to always work with the lastest versions)

update Oct'25
```bash
npx install -g claude-flow@latest
npx install -g agentic-flow@latest
# and then
claude-flow init --force # (in project folder) 
# Run Claude Code without installation
npx @anthropic-ai/claude-code --dangerously-skip-permissions
```



# Run Claude Flow commands directly without installation
npx --y claude-flow@alpha init --force
or?
npx claude-flow@alpha init --force
npx claude-flow@alpha --help


#### Option B: Global Installation (Recommended for Long-Term Use)

```bash
# Install Claude Code globally
npm install -g @anthropic-ai/claude-code

# Install Claude Flow Alpha version globally
Install both claude-flow and agentic-flow
```bash
npm install -g claude-flow@latest
npm install -g agentic-flow@latest
and then
claude-flow init --force in project folder, 
```
this will give you access to all agents/skills and features from both claude-flow and agentic-flow
After init check 
claude mcp list
to see availble mcp’s

# Verify installations
node --version    # Should be 18+ (LTS)
npm --version     # Should be 9+
claude --version  # Should show Claude Code version
claude-flow --version  # Should show v2.0.0-alpha.53+
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

# Resume a session

After a crash or taking a break

```bash
npx @anthropic-ai/claude-code --dangerously-skip-permissions
claude -c --dangerously-skip-permissions
```
it will look at the memory and determine where it left off and then spawn new agents to start where it left off.

with input line, explain what happended and to continue where you were at (e.g. continue spawning the swarm, continue with the hive mind, etc)


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
```
Should get: 
 You can now use SPARC-enhanced commands like:
  - ./claude-flow sparc start - Start SPARC methodology session
  - ./claude-flow swarm "objective" --sparc - Run swarm with SPARC integration
  - Check .claude/commands/sparc/ for all SPARC-specific documentation

```bash
# OR initialize with full alpha features (recommended for Codespaces)
claude-flow init --force --hive-mind --neural-enhanced
```
 Quick Start Commands:
  - ./claude-flow hive-mind init - Initialize hive mind collective
  - ./claude-flow hive-mind spawn "task" --neural - Spawn with neural optimization
  - ./claude-flow swarm "objective" --hive-mind --neural - Full enhanced swarm
  - ./claude-flow neural train - Train neural patterns

```bash
# Configure Claude Code integration with all 87 MCP tools
claude-flow mcp setup --auto-permissions --87-tools
```

This creates:
- `.claude/` directory with configuration
- `CLAUDE.md` (project instructions)
- `.roomodes` (pre-configured SPARC modes)
- MCP server configuration with advanced tools

 To start using these tools, run:
  - ./claude-flow mcp start --auto-orchestrator --daemon - Start MCP server
  - ./claude-flow swarm init --topology=mesh - Initialize swarm
  - ./claude-flow agent spawn coder --neural - Spawn neural-enhanced agent


## Github repo setup

## Step 3: Initialize Claude Flow with GitHub Integration

```bash
npx claude-flow@alpha init --github
```

## Start a project with SPARC methodology
see @sparc_methodology_guide
recommend making a requirements doc first and copy it into a /docs folder in the project and then tell Claude code to use that document along with what you want to build. by following the commands you want in the guide.

## Advanced MCP Integration Setup

### Sublinear Temporal System Integration

Reuven's sublinear-time-solver provides advanced temporal prediction and O(log n) algorithmic capabilities for high-performance computing tasks within Claude Flow systems.

#### Installation

```bash
# Install the main sublinear solver globally
npm install -g sublinear-time-solver

# Install temporal lead solver globally  
npm install -g temporal-lead-solver
```
 The package is now available system-wide and can be used with commands like:
  - sublinear-time-solver (if it provides a CLI)
  - Or imported in any Node.js project
```bash
# Verify installations
sublinear-time-solver --version
temporal-lead-solver --version
```

```bash
# Quick test (no installation needed)
npx sublinear-time-solver --help
```

#### MCP Configuration for Claude Code

Add to your `.claude/mcp.json`:

```json
{
  "mcpServers": {
    "sublinear-solver": {
      "command": "npx",
      "args": ["sublinear-time-solver", "mcp"],
      "capabilities": {
        "tools": true
      },
      "metadata": {
        "name": "sublinear-solver",
        "version": "1.4.1",
        "description": "Sublinear-time solver with temporal prediction capabilities"
      }
    }
  }
}
```

#### Available MCP Tools

Once configured, these high-performance tools become available in Claude Code:

- **solveTrueSublinear** - TRUE O(log n) solver using Johnson-Lindenstrauss dimension reduction
- **analyzeTrueSublinearMatrix** - Check matrix solvability and get complexity guarantees
- **temporalPredict** - Advanced temporal prediction with nanosecond precision
- **matrixSolve** - High-performance sparse matrix solving
- **pageRank** - Sublinear PageRank computation
- **benchmarkMethods** - Performance benchmarking across different algorithms

#### Usage Examples in Claude Code

```typescript
// TRUE O(log n) solver with dimension reduction
const result = await solveTrueSublinear({
  matrix: {
    values: [4, -1, -1, 4, -1, -1, 4],
    rowIndices: [0, 0, 1, 1, 1, 2, 2],
    colIndices: [0, 1, 0, 1, 2, 1, 2],
    rows: 3, cols: 3
  },
  vector: [1, 0, 1],
  target_dimension: 16,  // JL reduction: n → O(log n)
  jl_distortion: 0.5
});

// Analyze matrix for sublinear solvability
const analysis = await analyzeTrueSublinearMatrix({
  matrix: { /* sparse format */ }
});

console.log(analysis.complexity_guarantee); // "O(log 1000)"
console.log(analysis.recommended_method);   // "sublinear_neumann"
```

#### Integration with Claude Flow

```bash
# Initialize Claude Flow with sublinear solver support
npx claude-flow@alpha init --force --hive-mind --neural-enhanced

# Configure MCP integration
claude mcp add sublinear-solver
npx sublinear-time-solver mcp start

# Test integration
claude-flow hive-mind spawn "optimize large-scale system" --claude --sublinear-enhanced
```

#### Temporal Prediction Capabilities

- **Nanosecond Precision**: 98ns tick overhead scheduling
- **High Throughput**: 11M+ tasks/second for real-time systems  
- **Temporal Consciousness**: Strange loop convergence patterns
- **WASM Acceleration**: Hardware-accelerated temporal algorithms
- **Hardware TSC Timing**: Direct CPU cycle counter access

Perfect for:
- High-frequency trading systems
- Real-time control systems
- Multi-agent coordination
- Consciousness simulation research
- Large-scale ML optimization

### Ruv Swarm MCP Integration

The ruv swarm MCP server is part of Reuven Cohen's ruv-FANN neural network library, providing distributed agent orchestration with neural networks for enhanced swarm intelligence.

#### Installation

```bash
# Option 1: Install globally
npm install -g ruv-swarm

# Option 2: Use with npx (no installation needed)
npx ruv-swarm mcp start --protocol=stdio
```

#### Configuration for Claude Code

Create or edit `.claude/mcp.json` in your project root:

```json
{
  "mcpServers": {
    "ruv-swarm": {
      "command": "npx",
      "args": ["ruv-swarm", "mcp", "start", "--protocol=stdio"],
      "capabilities": {
        "tools": true
      },
      "metadata": {
        "name": "ruv-swarm",
        "version": "0.1.0",
        "description": "Distributed agent orchestration with neural networks"
      }
    }
  }
}
```

#### Alternative Configuration (Script Wrapper)

For better control, create `mcp-server.sh` (Linux/Mac) or `mcp-server.bat` (Windows):

**Linux/Mac:**
```bash
#!/bin/bash
cd /path/to/your/project
exec npx ruv-swarm mcp start --protocol=stdio
```

**Windows:**
```batch
@echo off
cd /d "C:\path\to\your\project"
npx ruv-swarm mcp start --protocol=stdio
```

Then update `.claude/mcp.json`:
```json
{
  "mcpServers": {
    "ruv-swarm": {
      "command": "/path/to/mcp-server.sh",
      "capabilities": {
        "tools": true
      }
    }
  }
}
```

#### Available MCP Tools

Once configured, the following tools will be available in Claude Code:

1. **swarm_init** - Initialize a new swarm with specified topology
2. **swarm_status** - Get current status of all active swarms
3. **swarm_monitor** - Monitor swarm activity in real-time
4. **agent_spawn** - Create a new agent in the swarm
5. **agent_list** - List all agents in the swarm
6. **agent_metrics** - Get performance metrics for agents
7. **task_orchestrate** - Orchestrate a task across the swarm
8. **task_status** - Check the status of running tasks
9. **task_results** - Get results from completed tasks
10. **benchmark_run** - Run performance benchmarks
11. **features_detect** - Detect available system features
12. **memory_usage** - Monitor memory usage

#### Usage Examples in Claude Code

```typescript
// Initialize a mesh swarm with 10 agents
await swarm_init({
  topology: "mesh",
  maxAgents: 10,
  strategy: "balanced"
});

// Spawn a researcher agent
await agent_spawn({
  type: "researcher",
  name: "data-researcher-1",
  capabilities: ["web_search", "data_mining"]
});

// Orchestrate a complex task
await task_orchestrate({
  task: "Analyze system performance and generate optimization report",
  priority: "high",
  strategy: "adaptive",
  maxAgents: 3
});
```

## Using Claude Flow

### Basic Commands

```bash
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

5. **Sublinear Temporal System Issues**:
   - If sublinear solver tools are not available, check your `.claude/mcp.json` configuration
   - Verify installation: `npm list -g sublinear-time-solver` or `npx sublinear-time-solver --version`
   - Test MCP server: `npx sublinear-time-solver mcp` should start without errors
   - For WASM-related issues, ensure your environment supports WebAssembly
   - Check Node.js version compatibility (requires Node.js 18+)

6. **Ruv Swarm MCP Issues**:
   - If ruv-swarm tools are not available in Claude Code, check your `.claude/mcp.json` configuration
   - Verify installation: `npm list -g ruv-swarm` or try `npx ruv-swarm --version`
   - Test MCP server: `npx ruv-swarm mcp start --protocol=stdio` should start without errors
   - Ensure Claude Code can access the MCP server by restarting Claude Code after configuration changes
   - Check that Node.js can execute the ruv-swarm command from your project directory

## Important Notes

- Some GitHub integration commands documented in Claude Flow may not be fully implemented in the alpha version
- Use general swarm commands and direct Claude Flow interactions instead of specialized GitHub commands if you encounter "Unknown GitHub mode" errors
- The alpha version is under active development; features may change

## Additional Resources

- [Claude Flow GitHub Repository](https://github.com/ruvnet/claude-flow)
- [Claude Flow Wiki](https://github.com/ruvnet/claude-flow/wiki)
- [Installation Guide](https://github.com/ruvnet/claude-flow/wiki/Installation-Guide)
- [Quick Start Guide](https://github.com/ruvnet/claude-flow/wiki/Quick-Start)
- [Sublinear Time Solver Repository](https://github.com/ruvnet/sublinear-time-solver) - Advanced O(log n) solver with temporal prediction capabilities
- [Ruv-FANN Repository](https://github.com/ruvnet/ruv-FANN) - Neural network library containing the ruv-swarm MCP server by Reuven Cohen
- [Ruv Swarm MCP Documentation](https://github.com/ruvnet/ruv-FANN/blob/main/ruv-swarm/docs/MCP_USAGE.md) - Detailed usage guide for ruv-swarm MCP tools
- [Claude Flow Integration Guide](https://github.com/ruvnet/claude-flow/issues/745) - Unified AI orchestration setup guide
