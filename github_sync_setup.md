# GitHub Integration Setup for Claude Flow

## Overview

This guide explains how to set up GitHub integration with Claude Flow, allowing you to use AI-powered swarms to manage repositories, pull requests, issues, and releases.

## Prerequisites

- Claude Flow installed (`npx claude-flow@alpha`)
- GitHub account with repository access
- Terminal or command prompt access

## Step 1: Create a GitHub Personal Access Token (PAT)

1. **Log in to GitHub** and go to your account settings
2. **Navigate to Developer Settings**:
   - Click on your profile picture in the top right
   - Select "Settings"
   - Scroll down and click on "Developer settings" in the left sidebar

3. **Access Personal Access Tokens**:
   - Click on "Personal access tokens"
   - Select "Fine-grained tokens" (recommended) or "Classic tokens"

4. **Generate a new token**:
   - Click "Generate new token"
   - For fine-grained tokens: Give it a name, set an expiration, and select the specific repositories you want to access
   - For classic tokens: Give it a name, set an expiration, and select the required scopes

5. **Set permissions**:
   - For Claude Flow GitHub integration, you'll need permissions for:
     - Repository contents (read/write)
     - Pull requests (read/write)
     - Issues (read/write)
     - If using workflows: Workflow permissions

6. **Generate the token**:
   - Click "Generate token" at the bottom
   - **Important**: Copy the token immediately as GitHub will only show it once

## Step 2: Add the Token to Your Environment

Choose one of these methods to add your token to your environment:

### Option 1: Direct export in terminal (temporary, session only)

```bash
export GITHUB_TOKEN=ghp_your_token_here
```

### Option 2: Add to .env file (more permanent)

```bash
echo "GITHUB_TOKEN=ghp_your_token_here" >> .env
```

### Option 3: Add to your shell profile (most permanent)

Add the export command to your `~/.bashrc`, `~/.zshrc`, or equivalent:

```bash
echo 'export GITHUB_TOKEN=ghp_your_token_here' >> ~/.bashrc
source ~/.bashrc  # to reload the file
```

## Step 3: Initialize Claude Flow with GitHub Integration

```bash
npx claude-flow@alpha init --github
```

## Step 4: Verify GitHub Integration

To verify your GitHub integration is working or to have claude set it up,then:

```bash
# Check repository information
npx claude-flow@alpha github repo-architect "Check repository structure"
```
This should set up the github workflow and create the CLI

# Or try a simple PR listing
npx claude-flow@alpha github pr-manager "List pull requests

You should see output confirming successful authentication and connection to your GitHub account. The command requires an objective parameter that describes what you want to do.

## Using GitHub Integration with Claude Flow

### Important Note About GitHub Commands

The documentation in this guide describes the intended functionality of Claude Flow's GitHub integration. However, **the current alpha version may have limited GitHub functionality** compared to what's described in the documentation.

When you try commands like `github issue-solver`, you might receive an error: `Unknown GitHub mode: issue-solver`. This indicates that some features are still being implemented or may require additional setup.

### Solving GitHub Issues Using Swarms

Instead of using specific GitHub commands that may not be available yet, you can use the general swarm command to work with GitHub issues:

```bash
# Use a swarm to analyze and solve a GitHub issue
npx claude-flow@alpha swarm "Analyze and fix GitHub issue #1" --research

# Create a solution for a specific issue
npx claude-flow@alpha swarm "Implement a solution for issue #1" --strategy development
```

### Alternative GitHub Workflow

You can also use Claude Flow to assist with GitHub workflows manually:

```bash
# Get Claude Flow to analyze a GitHub issue
npx claude-flow@alpha "Analyze GitHub issue #123 and suggest solutions"

# Generate code for a PR
npx claude-flow@alpha "Generate code for a PR that implements feature X"
```

### Complete Workflow Example

```bash
# 1. Create issue (if it doesn't exist)
npx claude-flow@alpha "Create GitHub issue for adding user authentication"

# 2. Implement with swarm
npx claude-flow@alpha swarm "Implement user authentication from issue #123" \
  --link-issue 123

# 3. Create PR
npx claude-flow@alpha "Create PR for implementing user authentication from issue #123"

# 4. Coordinate review
npx claude-flow@alpha "Coordinate review for PR #456"

# 5. Merge and release
npx claude-flow@alpha "Merge PR #456 and release v2.1.0"
```

## Additional Integration Tokens

When working with GitHub integration, you may encounter messages about configuring additional tokens for enhanced functionality:

### Codecov and Snyk Integration

You might see this message: "Remember to configure the required secrets (CODECOV_TOKEN, SNYK_TOKEN) in your GitHub repository settings for full functionality."

These tokens provide additional capabilities:

1. **CODECOV_TOKEN**: For [Codecov](https://codecov.io/) integration, which provides code coverage reporting to show how much of your code is being tested.

2. **SNYK_TOKEN**: For [Snyk](https://snyk.io/) integration, a security platform that helps find and fix vulnerabilities in your code, dependencies, and containers.

To configure these tokens in your GitHub repository:

1. Go to your repository on GitHub
2. Click on "Settings"
3. In the left sidebar, click on "Secrets and variables" → "Actions"
4. Click "New repository secret"
5. Add each token with its appropriate name (CODECOV_TOKEN or SNYK_TOKEN) and value

Note: These integrations are optional and enhance your workflow with automated code quality and security checks, but they're not required for the core GitHub functionality with Claude Flow.

## Security Best Practices

1. **Never commit your GitHub token** to a public repository
2. **Set an expiration date** for your token
3. **Use the principle of least privilege** - only grant the permissions needed
4. **Rotate tokens periodically** for enhanced security
5. **Consider using GitHub's organization secrets** for team environments

## Troubleshooting

### Common Issues

1. **Authentication Errors**
   - Verify your token has the correct permissions
   - Check that the token is correctly set in your environment
   - Ensure the token hasn't expired

2. **Repository Access Issues**
   - Confirm your token has access to the specific repositories
   - Check organization permissions if working with org repositories

3. **Rate Limiting**
   - GitHub API has rate limits; if you hit them, wait or use authenticated requests

### Getting Help

For additional assistance, run:

```bash
npx claude-flow@alpha help github
```

Or visit the Claude Flow documentation for more detailed information.