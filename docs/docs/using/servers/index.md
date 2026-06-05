# Sample MCP Servers

The ContextForge Gateway includes sample MCP servers for testing, development, and integration validation. These servers demonstrate MCP transports and provide deterministic targets for gateway federation, tool routing, and performance checks.

## Available Servers

### Rust

#### Fast Time Server

`mcp-servers/rust/fast-time-server` provides a high-performance Streamable HTTP MCP server with time, echo, and statistics tools.

```bash
cd mcp-servers/rust/fast-time-server
cargo build --release
BIND_ADDRESS=0.0.0.0:8880 ./target/release/fast-time-server
```

### Python

Python sample servers live under `mcp-servers/python/` and cover data analysis, diagram generation, evaluation, sandboxed Python execution, QR code generation, RSS search, output schema validation, and URL-to-markdown conversion.

## Gateway Integration

All sample servers are designed to integrate with ContextForge:

```bash
export BASE_URL="http://localhost:4444"

curl -X POST -H "Authorization: Bearer $MCPGATEWAY_BEARER_TOKEN" \
     -H "Content-Type: application/json" \
     -d '{"name":"fast_time","url":"http://localhost:8880/mcp","transport":"STREAMABLEHTTP"}' \
     "$BASE_URL/gateways"
```

## Development Guidelines

New sample servers should include tests, container-ready packaging when appropriate, health checks for web transports, and usage documentation. Prefer the existing Python and Rust patterns in this directory before adding new structure.

## Resources

- [Model Context Protocol](https://modelcontextprotocol.io/)
- [JSON-RPC 2.0 Specification](https://www.jsonrpc.org/specification)
- [ContextForge Gateway](../../index.md)
- [mcpgateway.wrapper Usage](../mcpgateway-wrapper.md)
- [mcpgateway.translate Bridge](../mcpgateway-translate.md)
