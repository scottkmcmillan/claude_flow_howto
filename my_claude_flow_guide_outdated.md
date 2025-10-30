From video
https://video.agentics.org/media/t/1_g53hho3n


# Gihub Codespace

RECOMMENDS using Github Codespace to use Swarms so you don't have swarms running on a local machine. Which can lead to a lot of issues, as the swarms work can overwhelm the local machine. Linux could be an option as it is more containerized but still not recommended. 

# claude code

## 1. Install Claude Code globally
npm install -g @anthropic-ai/claude-code

Logging out of claude code once installed is 
claude /logout

## 2. Activate Claude Code with permissions
claude --dangerously-skip-permissions

Use npm for claude code (does a global install)

!! remember that claude code doesn't authenticate the first time, you get an error. so go back to the terminal and open the link provided and it should work, then copy the code and paste it back into the terminal where prompted by claude code.

#1 if you use suscription, select #2 if use api

# Claude Flow
Use npx for claude flow since it is being regularly updated and this way you get the most recent version
(only needs to be done once in the codespace, then have it in that workspace to access via npx)




17:00 - starts installing claude flow

# Help
claude-flow@alpha --help

# Hive Mind Wizard

!! run in a new interactive terminal session otherwise the wizard runs automatically without input

npx claude-flow@alpha hive-mind wizard

Gives you more control over what the swarm will do

Hive mind is good at open ended and finds best solution for the problem

Swarm is better when you have a plan for the architecture and requirements

Wizard settings
Consensus algorithm - currently uses Majority - simple majorirty voting 
Enable auto scaling Yes

Another way instead of using the wizard or to add to it
Open claude /help to see all the commands
can then add those to the CLAUDE.md file based on how you want the system to work

# Spawn a new swarm

npx claude-flow@alpha hive-mind spawn "build me a REST API" --claude

INCLUDE --claude at the end to kickoff claude to work on the swarm.


# Hive.db file

This is the database for the hive mind. so see multiple tables with decisions etc being made


# Github Integration

Two options
1. Use the github CLI
2. Use claude mcp (seems better)
get token, configure it in mcp
ask claude how to do it
Codespace has this all installed

# Resume a session

After a crash or taking a break

claude -c --dangerously-skip-permissions
it will look at hte memory and determine where it left off and then spawn new agents to start where it left off.

with input line, explain what happended and to continue where you were at (e.g. continue spawning the swarm, continue with the hive mind, etc)


