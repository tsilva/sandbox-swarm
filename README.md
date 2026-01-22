<div align="center">
  <img src="logo.png" alt="sandbox-swarm" width="512"/>

  **🐝 Sandbox for experimenting with OpenAI Swarm multi-agent framework**

</div>

## Overview

A sandbox for experimenting with OpenAI Swarm, a framework for building multi-agent systems. Demonstrates basic agent coordination patterns where agents can transfer control to each other based on context.

## Features

- **Agent handoff** - Agents transfer control based on context
- **Custom behaviors** - Define agent-specific instructions
- **Function tools** - Enable agent coordination through functions
- **Simple orchestration** - Swarm client manages agent execution

## Quick Start

```bash
# Clone and setup
git clone https://github.com/tsilva/sandbox-swarm.git
cd sandbox-swarm

# Create environment
conda env create -f environment.yml
conda activate sandbox-swarm

# Configure API key
cp .env.example .env
# Edit .env with your OPENAI_API_KEY

# Run the demo
python main.py
```

## Architecture

```python
# Define agents with name, instructions, and functions
agent_a = Agent(
    name="Agent A",
    instructions="...",
    functions=[transfer_to_agent_b]
)

# Run with Swarm client
response = client.run(agent=agent_a, messages=[...])
```

## Requirements

- Python 3.10
- Conda
- OpenAI API key

## License

MIT
