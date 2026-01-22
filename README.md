<div align="center">
  <img src="logo.png" alt="sandbox-swarm" width="512"/>

  # sandbox-swarm

  [![Python 3.10](https://img.shields.io/badge/Python-3.10-blue.svg)](https://www.python.org/downloads/)
  [![OpenAI Swarm](https://img.shields.io/badge/OpenAI-Swarm-412991.svg)](https://github.com/openai/swarm)
  [![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

  **A sandbox for experimenting with OpenAI Swarm's multi-agent coordination patterns**

  [Swarm Documentation](https://github.com/openai/swarm)
</div>

## Overview

This repository demonstrates basic agent coordination patterns using OpenAI's Swarm framework. Agents can transfer control to each other based on context, enabling dynamic multi-agent workflows.

## Features

- Agent handoff demonstration between specialized agents
- Simple agent definitions with custom instructions
- Transfer functions for dynamic agent switching
- Environment variable management with python-dotenv

## Quick Start

```bash
# Clone and setup
git clone https://github.com/tsilva/sandbox-swarm.git
cd sandbox-swarm
conda env create -f environment.yml
conda activate sandbox-swarm

# Configure API key
cp .env.example .env
# Edit .env and add your OPENAI_API_KEY

# Run the demo
python main.py
```

## Installation

### Prerequisites

- [Conda](https://docs.conda.io/en/latest/miniconda.html) or [Mamba](https://mamba.readthedocs.io/)
- OpenAI API key

### Environment Setup

1. Create the conda environment:
   ```bash
   conda env create -f environment.yml
   ```

2. Activate the environment:
   ```bash
   conda activate sandbox-swarm
   ```

3. Configure your API key:
   ```bash
   cp .env.example .env
   ```
   Edit `.env` and add your `OPENAI_API_KEY`.

## Usage

The main example demonstrates agent handoff:

```python
from swarm import Swarm, Agent

client = Swarm()

def transfer_to_agent_b():
    return agent_b

agent_a = Agent(
    name="Agent A",
    instructions="You are a helpful agent.",
    functions=[transfer_to_agent_b],
)

agent_b = Agent(
    name="Agent B",
    instructions="Only speak in Haikus.",
)

response = client.run(
    agent=agent_a,
    messages=[{"role": "user", "content": "I want to talk to agent B."}],
)

print(response.messages[-1]["content"])
```

When you run `python main.py`, Agent A receives the request and transfers control to Agent B, which responds in haiku form.

## Architecture

```
┌─────────────┐     transfer_to_agent_b()     ┌─────────────┐
│   Agent A   │ ──────────────────────────────▶│   Agent B   │
│  (Helper)   │                                │  (Haikus)   │
└─────────────┘                                └─────────────┘
       ▲                                              │
       │                                              │
       │              Swarm Client                    │
       └──────────────────────────────────────────────┘
```

**Key Components:**

| Component | Description |
|-----------|-------------|
| `Swarm` client | Orchestrates agent execution and message handling |
| `Agent` | Defined with name, instructions, and optional functions |
| Transfer functions | Enable dynamic agent handoff based on context |

## References

- [OpenAI Swarm](https://github.com/openai/swarm) - Official framework documentation

## License

MIT
