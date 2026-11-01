# ms-toolbox

Self-contained microservice toolbox. Drop into any Python project.

## Quick start

```bash
# list all services
python cli.py list

# describe a service (full JSON schema)
python cli.py describe ScoutMS

# call an endpoint
python cli.py call ScoutMS scan_path root_path=/some/dir depth=3
```

## MCP server

Wire into Claude Desktop or any MCP client:

```json
{
  "mcpServers": {
    "ms-toolbox": {
      "command": "python",
      "args": ["/absolute/path/to/ms_toolbox/mcp_server.py"]
    }
  }
}
```

Requires: `pip install mcp`

Each `@service_endpoint` becomes an MCP tool named `ServiceName__method_name`.

## Structure

```
ms_toolbox/
  services/           <- service files + runtime (microservice_std_lib, base_service)
  cli.py              <- CLI entry point
  mcp_server.py       <- MCP stdio server
  codex.md            <- full service index for agent lookup
  pyproject.toml
```
