# Basic Math MCP Server

A simple yet powerful MCP server built using the [FastMCP framework](https://pypi.org/project/mcp-server/) that enables basic math operations like addition, subtraction, multiplication, and division — usable right inside Claude Desktop or any MCP-compatible environment.

---

## What is MCP?

**MCP (Model Context Protocol)** is an open standard developed by Anthropic that allows external tools, APIs, or scripts to be exposed to large language models (LLMs) like Claude in a structured and interactive way.

With MCP, developers can:
- Build custom tools accessible by language models.
- Extend capabilities of Claude with Python scripts or microservices.
- Share structured data or custom responses via `@tool()` and `@resource()` decorators.

---

## What is a Custom MCP Server?

A **Custom MCP Server** is a Python-based service that implements the MCP specification using the `mcp-server` library. These servers:
- Define callable tools (`@tool`) for computation or automation.
- Host resources (`@resource`) like documentation or reference data.
- Run locally or remotely, responding to MCP clients such as Claude Desktop.

MCP servers enable low-latency, secure, and contextual integration between your own code and the capabilities of LLMs.

---

## What We’ve Built

This project is a minimal but complete MCP server offering basic arithmetic capabilities. Tools exposed:

### Tools:
- `add(a, b)` – Returns the sum of two numbers.
- `subtract(a, b)` – Returns the result of subtracting `b` from `a`.
- `multiply(a, b)` – Returns the product of `a` and `b`.
- `divide(a, b)` – Returns the quotient of `a` divided by `b`. Handles division by zero.

### Resources:
- `calculator://help` – A Markdown-formatted help file that explains usage of all tools.

---

## Prerequisites

Before getting started, make sure you have the following installed:

- Python 3.9+
- Claude Desktop (or any MCP-compatible interface)
- [uv](https://github.com/astral-sh/uv) runtime (for fast, isolated Python execution)

---

## Installation Steps

### Step 1: Install `uv` (required to run MCP servers)

#### macOS/Linux:
```bash
curl -Ls https://astro.build/install/uv | bash
```
This will install `uv` to `~/.local/bin/uv`

#### Windows (PowerShell):
```powershell
irm https://astro.build/install/uv.ps1 | iex
```
You may need to restart your terminal or add `uv` to PATH.

---

### Step 2: Install the MCP Server

Use `uv` to install `mcp-server` and run your server:
```bash
uv pip install mcp-server
```

To run the server manually:
```bash
uv run mcp-server
```

---

## Integration with Claude Desktop

Once installed, you need to configure Claude to discover this MCP server.

### Locate `claude_desktop_config.json`
This file holds MCP server configurations for Claude Desktop. Add or update as below.

### If You Don’t Have Any MCP Servers:
Paste this entire block into your config:
```json
{
  "mcpServers": {
    "mcp-server": {
      "command": "uv",
      "args": [
        "run",
        "mcp-server"
      ]
    }
  }
}
```

### If You Already Have MCP Servers:
Just add the following entry to the "mcpServers" object:
```json
"mcp-server": {
  "command": "uv",
  "args": [
    "run",
    "mcp-server"
  ]
}
```

Make sure your JSON stays valid (e.g., commas between entries).

---

## Usage Examples

![Usage Example](https://github.com/user-attachments/assets/cdf75f14-b79c-4c03-b54b-e2329b4be716)

This image illustrates how the Basic Math MCP Server works in real-time with Claude Desktop.

---

## Tool Help Resource

You can also use the built-in help:
```plaintext
resource: calculator://help
```

It returns markdown-formatted instructions for all tools.

---

## Useful Links

- PyPI: [MCP-Server](https://pypi.org/project/mcp-server/)
- Claude + MCP Docs: [Official Anthropic Guide](https://docs.anthropic.com/claude/docs/custom-mcp-tools)
- GitHub UV Runtime: [https://github.com/astral-sh/uv](https://github.com/astral-sh/uv)

---



