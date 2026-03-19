# GDG_ADK_Lab_2: Multi-Agent Systems

A comprehensive multi-agent system project demonstrating advanced agent orchestration patterns using Google's Agent Development Kit (ADK) and Gemini models.

## Overview

This project showcases two main agent architectures:
- **Parent and Subagents**: Hierarchical agent relationships with parent-child agent patterns
- **Workflow Agents**: Sequential, parallel, and loop-based agent workflows

## Project Structure

```
GDG_ADK_Lab_2/
├── adk_multiagent_systems/
│   ├── parent_and_subagents/          # Parent-child agent implementation
│   │   ├── agent.py                    # Agent definitions
│   │   ├── .env                        # Configuration (add your API key)
│   │   └── __init__.py
│   ├── workflow_agents/                # Workflow-based agents
│   │   ├── agent.py                    # Agent definitions
│   │   ├── .env                        # Configuration (add your API key)
│   │   └── __init__.py
│   ├── callback_logging.py             # Logging utilities for model callbacks
│   └── requirements.txt                # Project dependencies
├── adk_utils/
│   ├── plugins.py                      # Graceful429Plugin and utilities
│   └── __init__.py
├── myenv/                              # Python virtual environment
├── .gitignore                          # Git ignore rules
└── README.md                           # This file
```

## Features

- **Hierarchical Agent Patterns**: Parent agents that delegate tasks to subagents
- **Workflow Automation**: Sequential, parallel, and loop-based agent orchestration
- **Callback Logging**: Track model queries and responses in real-time
- **Error Handling**: Built-in retry mechanisms and graceful error handling
- **Local or Cloud Inference**: Support for both local Gemini API and Google Cloud VertexAI

## Requirements

- Python 3.8+
- Google Gemini API key (for local inference)
- Dependencies listed in `adk_multiagent_systems/requirements.txt`

## Setup

### 1. Create and Activate Virtual Environment

```bash
python -m venv myenv
# On Windows:
myenv\Scripts\activate
# On macOS/Linux:
source myenv/bin/activate
```

### 2. Install Dependencies

```bash
cd adk_multiagent_systems
pip install -r requirements.txt
```

### 3. Configure API Keys

Update the `.env` files in each agent folder with your Gemini API key:

**parent_and_subagents/.env:**
```
GOOGLE_GENAI_USE_VERTEXAI=FALSE
GOOGLE_API_KEY=your_api_key_here
MODEL=gemini-2.5-flash
```

**workflow_agents/.env:**
```
GOOGLE_GENAI_USE_VERTEXAI=FALSE
GOOGLE_API_KEY=your_api_key_here
MODEL=gemini-2.5-flash
```

## Usage

### Running Parent and Subagents

```bash
cd adk_multiagent_systems
adk run parent_and_subagents
```

### Running Workflow Agents

```bash
cd adk_multiagent_systems
adk run workflow_agents
```

## Configuration

### Environment Variables

- `GOOGLE_GENAI_USE_VERTEXAI`: Set to `FALSE` for local API, `TRUE` for Google Cloud
- `GOOGLE_API_KEY`: Your Gemini API key (for local inference)
- `GOOGLE_CLOUD_PROJECT`: GCP project ID (for VertexAI)
- `GOOGLE_CLOUD_LOCATION`: GCP region (for VertexAI)
- `MODEL`: Model name (e.g., `gemini-2.5-flash`)

## Key Components

### Callback Logging
The `callback_logging.py` module provides hooks to log:
- Query prompts sent to the model
- Model responses
- Function calls made by agents

### Plugins
The `Graceful429Plugin` in `adk_utils/plugins.py` handles rate-limiting gracefully.

## Development

To add new agents:
1. Define your agent in the appropriate `agent.py` file
2. Use the `@agent` decorator with required parameters
3. Configure callbacks for logging if needed
4. Test with `adk run <agent_name>`

## License

This project is part of GDG ADK Lab 2
