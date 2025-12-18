# Prompt Engineer & Project Orchestrator

This project hosts the core persona and configuration for your **Prompt Engineer & Project Orchestrator** agent. When you run Gemini CLI from this directory, it will adopt this persona, enabling it to:

1.  **Design Project Prompts:** Collaborate with you to define project requirements and generate tailored "master prompts" for specialist AI agents.
2.  **Scaffold Projects:** Automatically create new project directories, complete with the master prompt and necessary project-specific MCP server configurations.
3.  **Manage MCP Domains:** Administratively handle the addition and updating of MCP server domain definitions in `mcp_config_index.json`.

## Getting Started

1.  **Navigate:** Change your current directory to this project's root:
    ```bash
    cd /home/brendan/projects/prompt-engineer
    ```
2.  **Start Gemini:** Run your Gemini CLI instance from this directory.

## Key Files & Directories

*   **`GEMINI.md`**: This file contains the complete persona definition for the Prompt Engineer & Project Orchestrator. It dictates how the agent behaves, its responsibilities, and its interaction flow.
*   **`mcp_config_index.json`**: This JSON file acts as the central index for all known MCP (Micro-Component Provider) domain configurations. The Orchestrator reads this to determine which MCP servers are needed for a given project.
*   **`new_domain_template.yml`**: A YAML template for easily defining and adding new MCP domains (and their associated MCP servers) to the `mcp_config_index.json` file.
*   **`personas/`**: This directory stores individual specialist persona definitions (e.g., `n8n-engineer.md`, `aws-architect.md`). The Orchestrator selects the most appropriate persona from here when assembling a master prompt.
    *   **`personas/n8n-engineer.md`**: An example specialist persona for n8n workflow development.

## How to Use

### 1. Scaffolding a New Project

Engage the Orchestrator in conversation about your new project. Describe its purpose, technologies, and desired outcomes. The Orchestrator will:
*   Ask clarifying questions.
*   Identify relevant specialist personas.
*   Determine required MCP domains.
*   Propose a master prompt and seek your approval to scaffold the project directory.

Example interaction:
```
User: "I need to set up a new project to build an n8n workflow that connects to an external API and processes data with custom JavaScript."
Agent: (will converse, clarify, and eventually propose scaffolding)
```

### 2. Managing MCP Domains

To add a new MCP domain or update an existing one in `mcp_config_index.json`:

1.  Create a new YAML file (e.g., `my_new_domain.yml`) based on the structure of `new_domain_template.yml`.
2.  Fill in the `domain_name`, `description`, and `mcp_servers` details.
3.  Ask the Orchestrator to process your file:
    ```
    User: "Please process this file: `my_new_domain.yml`."
    Agent: (will follow the instructions in the template to update `mcp_config_index.json`)
    ```
    
