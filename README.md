# AI Agent set up

## What it includes

A custom agent to generate project description and instructions inside:

- [copilot-instructions.md](https://docs.github.com/en/copilot/how-tos/copilot-on-github/customize-copilot/add-custom-instructions/add-repository-instructions)
- [AGENTS.md](https://agents.md/)

## Why I create it

- The need of a shareable custom agent to generate basic agent instruction md file based on [github official instruction](https://docs.github.com/en/copilot/how-tos/copilot-on-github/customize-copilot/add-custom-instructions/add-repository-instructions#asking-copilot-cloud-agent-to-generate-a-copilot-instructionsmd-file)

- The basic agent instruction md file lay the groundwork for SDD (spec driven development)

## How it works

1. Copy `.github/agents/agent-instruction-creator.agent.md` to your repository's `.github/agents/` directory.

2. Select the newly created `agent-instruction-creator-agent` agent and run:

```
generate
```

3. The agent analyzes your project and generates instruction files automatically
