
```markdown
# Math Calculator MCP Server

A custom MCP server that provides mathematical calculation tools and resources for AI assistants.

## Components

### Tools
The server provides basic and advanced mathematical operations:

- **add**: Add two numbers together
- **subtract**: Subtract the second number from the first
- **multiply**: Multiply two numbers together
- **divide**: Divide the first number by the second
- **calculate_percentage**: Calculate a percentage of a value
- **power**: Raise a number to a specified power
- **square_root**: Calculate the square root of a number

### Resources
The server provides reference formulas as resources:

- **formula://area**: Common formulas for calculating area of different shapes
- **formula://volume**: Common formulas for calculating volume of different 3D shapes
- **formula://trigonometry**: Common trigonometric formulas and identities

### Prompts
The server includes templates for solving mathematics problems:

- **solve_math_problem**: Template for solving math word problems step by step
- **formula_application**: Template for applying a specific formula to solve a problem

## Configuration

### Environment Variables
This server doesn't require any specific environment variables.

## Quickstart

### Install

#### Claude Desktop
On MacOS: `~/Library/Application\ Support/Claude/claude_desktop_config.json`
On Windows: `%APPDATA%/Claude/claude_desktop_config.json`

<details>
<summary>Development/Unpublished Servers Configuration</summary>

```json
"mcpServers": {
  "mcp-server": {
    "command": "uv",
    "args": [
      "--directory",
      "/Users/Ajinkya25/Documents/Idea-Labs/MCP/mcp-server",
      "run",
      "mcp-server"
    ]
  }
}
```
</details>

<details>
<summary>Published Servers Configuration</summary>

```json
"mcpServers": {
  "mcp-server": {
    "command": "uvx",
    "args": [
      "mcp-server"
    ]
  }
}
```
</details>

## Development

### Testing Locally
To test the server locally:

```bash
# Activate the virtual environment (if not already activated)
source .venv/bin/activate  # On macOS/Linux

# Test the server in development mode
mcp dev -m mcp_server.server
```

### Building and Publishing
To prepare the package for distribution:

1. Sync dependencies and update lockfile:
```bash
uv sync
```

2. Build package distributions:
```bash
uv build
```
This will create source and wheel distributions in the `dist/` directory.

3. Publish to PyPI:
```bash
uv publish
```

Note: You'll need to set PyPI credentials via environment variables or command flags:
- Token: `--token` or `UV_PUBLISH_TOKEN`
- Or username/password: `--username`/`UV_PUBLISH_USERNAME` and `--password`/`UV_PUBLISH_PASSWORD`

### Debugging
Since MCP servers run over stdio, debugging can be challenging. For the best debugging
experience, we strongly recommend using the [MCP Inspector](https://github.com/modelcontextprotocol/inspector).

You can launch the MCP Inspector via [`npm`](https://docs.npmjs.com/downloading-and-installing-node-js-and-npm) with this command:
```bash
npx @modelcontextprotocol/inspector uv --directory /Users/Ajinkya25/Documents/Idea-Labs/MCP/mcp-server run mcp-server
```

Upon launching, the Inspector will display a URL that you can access in your browser to begin debugging.

## License

MIT
```

## Testing Your MCP Server

Now let's make sure your MCP server works properly:

1. Save the updated code to `src/mcp_server/server.py`
2. Save the updated README.md
3. Test your server using:

```bash
mcp dev -m mcp_server.server
```

This should open the MCP Inspector in your browser where you can try out your math tools.

## Publishing to PyPI

Once you've tested your server and confirmed it works, you can publish it to PyPI:

1. Make sure you have a PyPI account (register at https://pypi.org/account/register/ if needed)
2. Build your package:

```bash
uv build
```

3. Publish to PyPI:

```bash
uv publish --token YOUR_PYPI_TOKEN
```

Or if you prefer to use username/password:

```bash
uv publish --username YOUR_USERNAME --password YOUR_PASSWORD
```

After publishing, anyone can install your MCP server using:

```bash
pip install mcp-server
```

And then use it with Claude Desktop by configuring their claude_desktop_config.json as shown in the README.