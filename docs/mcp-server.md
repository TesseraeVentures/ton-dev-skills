# MCP Server

The TON Dev Toolkit MCP server exposes all toolkit features as tools for AI assistants (Claude, Cursor, Windsurf, etc.).

**Requires Pro or Enterprise plan.**

## Available Tools

| Tool | Description |
|------|-------------|
| `ton_audit` | Run security audit on a contract file or source string |
| `ton_migrate` | Migrate a Solidity contract to TON-native |
| `ton_scaffold` | Generate a new contract from template |
| `ton_compile` | Compile a FunC/Tact/Tolk contract |
| `ton_deploy` | Deploy a compiled contract to testnet/mainnet |
| `ton_tep_check` | Check TEP compliance for a contract |
| `ton_fetch_contract` | Fetch on-chain contract code by address |
| `ton_disassemble` | Disassemble a BOC to human-readable TVM instructions |
| `ton_test_gen` | Generate test cases for a contract |

## Setup

### Claude Desktop

Add to `~/Library/Application Support/Claude/claude_desktop_config.json`:

```json
{
  "mcpServers": {
    "ton-dev": {
      "command": "ton-mcp",
      "args": ["start"]
    }
  }
}
```

### Cursor

Add to `.cursor/mcp.json` in your project:

```json
{
  "mcpServers": {
    "ton-dev": {
      "command": "ton-mcp",
      "args": ["start"]
    }
  }
}
```

### Windsurf / Other MCP Clients

```bash
# Start the server manually (stdio transport)
ton-mcp start

# Start with SSE transport on a specific port
ton-mcp start --transport sse --port 3100
```

## Transport Options

| Transport | Use Case |
|-----------|----------|
| `stdio` | Local IDE integration (default) |
| `sse` | Remote or shared access |

## Example Prompts

Once connected, try asking your AI assistant:

- "Audit `contracts/jetton.fc` for security issues"
- "Migrate `MyToken.sol` from Solidity to a TON Jetton"
- "Scaffold a new NFT collection called CoolCats"
- "Is this contract TEP-74 compliant?"
- "Fetch the contract at `EQC...` and check it for vulnerabilities"
- "Generate tests for my Jetton wallet contract"

See [API docs](api.md) for full tool schemas.
