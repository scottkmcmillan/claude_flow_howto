# Autonomous Swarm and Hive-mind Coding with Claude Flow

Once installed (see claude_flow_development_lifecycle.md), an example workflow is: 

1. Start a hive-mind to research how to build the application
```bash
npx claude-flow@alpha hive-mind spawn "build enterprise system" --claude
```

2. Review the results and make changes using Claude or a swarm
```bash
npx claude-flow@alpha swarm "chane the backend to do xyz" --claude
```

3. Create a swarm to write a sprint based development plan

!! Make sure the plan develops a CLI to run the application and be the interface to the system before developing a UI for it. !!

!! Make sure to use SQlite unless have a better reason to use another DB

!! Use Claude Code or Claude API for any AI integration

```bash
npx claude-flow@alpha swarm "write a sprint based development plan" --claude
```

4. Review the plan and use Claude Code, or a Swarm to make changes to the plan

5. Reverse engineer the requirements of the application now, to make sure it will do what is needed by using a swarm
```bash
npx claude-flow@alpha swarm "reverse engineer the requirements of the application" --claude
```

6. Write a user manual to further validate the system and requirements

7. Validate the development plan using a swarm by cross referencing it to the requirements and the research and the user manual

8. Validate the requirements and sprint development plan are aligned with the CLI user manual





