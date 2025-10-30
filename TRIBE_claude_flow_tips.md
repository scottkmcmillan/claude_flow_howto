# rUv Agentic Tribe Tips

SEE ALSO POSTS listed in this sheet:
https://docs.google.com/spreadsheets/d/1uCHaiCIvQw6eDCxSz58knPDeMB2k0K9b_izyc59DPF0/edit



## Tutorials

### Development Guide
see @saas_development_guide as a template to using Claude Code

## Keeping LLM alignment
Another trick I have learnt, ask the LLM what it's understanding is of a task is if you think it is starting to go off the rails. It's the easiest way to bring alignment back into focus between your goals and what it thinks those are.. almost always you'll find the LLM is already off on a tangent...Ask this question regularly

## Planning

### Context (requirement) gathering
I have this utility I built that takes several MD files of context that I “Like” which also includes a PLANS.md file that has the context of what I want to build, it takes all those files hands it off to claude and says, “Build me a an optimal CLAUDE.md for this project”. Has some pretty good results. It is def a hack though.. mostly untested.. https://github.com/marcuspat/turbo-flow-wizard 

check this out, works really well too along those lines: https://github.com/FlineDev/ContextKit 

### Developing requirements and specification leveraging claude flow
I use the SPARC approach. First, I utilize either deep research mode or specialized research agents to conduct research and develop a high-level requirements document in .md format.

Then I start a swarm of specialized agents to work on creating a detailed Specification documentation.
When the specification is done, I do a manual review first, and then use specialized agents to analyze the specification and compare it with the original requirements. This repeats until all is in sync. Next, using specification as grounding, I start a swarm of agents to work on writing Pseudocode per specifications.
Then, again, review phase, manual + agentic one, until all documents are in sync.
Next phase, creating Architecture documentation grounded in Specs and Pseudocode.
Then, again, review phase, manual + agentic one, until all documents are in sync.

Only then do I start the implementation and Refinement phase with a swarm of agents with a hive-mind overview, and they must work in the TDD way, write a test that fails, write the code so the test can pass, and refactor to make it better. This takes the longest. Depending on the app complexity, it can take from a couple to several dozen iterations to get to the working app. A lot of focus on preparing good tests and initial documentation helps a lot to finish faster.

The last phase is Completion, where I manually + agenticly test the app extensively, finish documentation, and prepare deployment to staging/production.
All this is done in VS Code terminal using Claude Code CLI + Claude Flow orchestration.

You can ask it to use SPARC agents to work on SPARC phases, then it will auto-assign SPARC agents.



## Claude flow vs Agentic Flow
Claude flow is the tools (agents.md files) and agentic flow is how to optimise your token usage between LLM's other than Claude. You can activate agentic flow when using claude flow

## Understanding Session Limites in Claude Code
From rUv: 

The video *“Claude Code New Session Limits: What Solo Devs Need to Know”* explains the updated usage and session system for Anthropic’s Claude tools, especially impacting solo developers [1].  

*Key learnings:*  
1. *Sessions are now time-based:* Each starts when you send the first message and lasts 5 hours, regardless of number of prompts. After that, a new session begins automatically [1].  
2. *Shared limits:* All tools under a user account—Claude chat, Claude Code, CLI—draw from the same session pool. No separation between chat and coding usage [1].  
3. *Plan differences:*  
   - *Pro ($20/month):* Unlimited sessions, but 45 messages or 10–40 code prompts per 5-hour window.  
   - *Max ($100/month):* 50 sessions per month; up to 225 messages or 50–200 prompts each.  
   - *Max Plus ($200/month):* 50 sessions; up to 900 messages or 200–800 prompts each [1].  
4. *Hidden constraint:* The main limiter isn’t message count but session count. Short, scattered check-ins waste sessions quickly, even if few messages are used [1].  
5. *Best practices:*  
   - Batch tasks and questions before starting a session.  
   - Use sessions for deep, focused work sprints.  
   - Avoid starting a new session if you can’t stay active within the 5-hour window.  
   - Keep alternate workflows (Cursor, Codeex, or offline coding) for cooldown periods [1].  
6. *Mindset shift:* The system encourages more intentional, structured, and productive development habits rather than impulsive, fragmented interaction with AI tools.


## Security for LLM applications

Sanitizes documents to prevent an LLM based application from getting corrupted. (Although I don't really understand the use cases and how this would happen)

https://gist.github.com/ruvnet/d0979347decadcffeac8a2b924c6ff8d


## GOAL planner agent
https://github.com/ruvnet/claude-flow/blob/main/.claude/agents/goal/goal-planner.md


## SPEC driven development

rUv goes straight to specificatiion using this methodology. I typically add a requirements phase before this. 

Spec-driven development works because it turns thought into architecture. A good specification is not just documentation; it is a living blueprint that defines how ideas become systems.

https://www.linkedin.com/posts/reuvencohen_spec-driven-development-works-because-it-share-7384579803548626944-z2UA?utm_source=share&utm_medium=member_ios&rcm=ACoAAAAsDPgBDJuUuadvvnSxPUkh_oT8zWlUvrk 

https://www.linkedin.com/posts/reuvencohen_spec-driven-development-works-because-it-share-7384579803548626944-z2UA?utm_source=share&utm_medium=member_ios&rcm=ACoAAAAsDPgBDJuUuadvvnSxPUkh_oT8zWlUvrk 

## Dev environments

### Fly.io low cost remote environment

https://github.com/pacphi/claude-flow-on-fly

## Networt multi-reasoning Agentic Flow
Sneak peak at tomorrow tutorial: 🚀 Agentic Flow 1.6.4 + QUIC: Make Your Network Think

Transform the internet into a multi-threaded reasoning fabric with a few CLI commands

https://gist.github.com/ruvnet/02fe6aee1aa8def78fd2661d8a1fa67d 

# Local Setups

https://claraverse.space/
And there is another one https://localai.io/ but looks to have less capabilities

