# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a sandbox repository for experimenting with OpenAI Swarm, a framework for building multi-agent systems. The project demonstrates basic agent coordination patterns where agents can transfer control to each other based on context.

## Environment Setup

**Conda Environment Management:**
- Create environment: `conda env create -f environment.yml`
- Activate environment: `conda activate sandbox-swarm`
- Environment name: `sandbox-swarm` (Python 3.10)

**Dependencies:**
- OpenAI Swarm (installed from GitHub: `git+https://github.com/openai/swarm.git`)
- python-dotenv for environment variable management

**Environment Variables:**
- Copy `.env.example` to `.env` and add your `OPENAI_API_KEY`
- Required: `OPENAI_API_KEY` must be set for the Swarm client to function

## Running the Code

Execute the main example:
```sh
python main.py
```

This runs a simple agent handoff demo where Agent A transfers to Agent B.

## Architecture

**Agent Pattern:**
The codebase demonstrates the Swarm framework's agent pattern:
- Agents are defined with `name`, `instructions`, and optional `functions`
- Functions enable agent handoff (e.g., `transfer_to_agent_b()`)
- The `Swarm` client orchestrates agent execution with `client.run(agent, messages)`
- Agents can be designed with specific behaviors (e.g., Agent B only speaks in Haikus)

**Main Entry Point:**
- `main.py` contains the complete example: agent definitions, handoff logic, and execution

## Swarm Framework Reference

Official documentation: https://github.com/openai/swarm

## Important Notes

- README.md must be kept up to date with any significant project changes
