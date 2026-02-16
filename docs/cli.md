# CLI Reference

## Commands

### `ton-audit`

Run a security audit on one or more contracts.

```
ton-audit <path> [options]

Arguments:
  path                Contract file or directory to audit

Options:
  --format <type>     Output format: terminal, json, sarif, markdown (default: terminal)
  --output <file>     Write report to file instead of stdout
  --severity <level>  Minimum severity: info, low, medium, high (default: info)
  --categories <list> Comma-separated categories to check (default: all)
  --no-color          Disable colored output
  -q, --quiet         Only output findings (no banner/summary)
  -h, --help          Show help
```

### `ton-migrate` (Pro)

Migrate an EVM contract to TON.

```
ton-migrate [options]

Options:
  --from <chain>      Source chain: solidity (default: solidity)
  --contract <path>   Path to source contract
  --lang <language>   Output language: tact, func (default: tact)
  --output <dir>      Output directory (default: ./output/)
  --dry-run           Show migration plan without generating files
  -h, --help          Show help
```

### `ton-scaffold`

Generate a new contract from a template.

```
ton-scaffold <template> [options]

Templates:
  jetton              Jetton master + wallet (TEP-74)
  nft-collection      NFT collection + item (TEP-62)
  sbt                 Soulbound token (TEP-85)
  dao                 DAO governance contract
  multisig            Multi-signature wallet
  dex-pool            DEX liquidity pool

Options:
  --name <name>       Contract/token name
  --symbol <symbol>   Token symbol
  --output <dir>      Output directory (default: ./)
  --lang <language>   Output language: tact, func (default: tact)
  -h, --help          Show help
```

### `ton-compile`

Compile a FunC, Tact, or Tolk contract.

```
ton-compile <path> [options]

Options:
  --output <file>     Output BOC file path
  -h, --help          Show help
```

### `ton-deploy`

Deploy a compiled contract.

```
ton-deploy <boc> [options]

Options:
  --network <net>     Network: testnet, mainnet (default: testnet)
  --wallet <path>     Path to wallet keys
  --amount <ton>      Initial TON balance (default: 0.05)
  -h, --help          Show help
```

### `ton-test-gen` (Pro)

Generate test cases for a contract.

```
ton-test-gen <path> [options]

Options:
  --framework <fw>    Test framework: sandbox, jest (default: sandbox)
  --output <dir>      Output directory
  -h, --help          Show help
```

### `ton-fetch`

Fetch on-chain contract code.

```
ton-fetch <address> [options]

Options:
  --network <net>     Network: testnet, mainnet (default: mainnet)
  --output <file>     Save to file
  --disasm            Also disassemble the code
  -h, --help          Show help
```

### `ton-mcp` (Pro)

Start the MCP server.

```
ton-mcp start [options]

Options:
  --transport <type>  Transport: stdio, sse (default: stdio)
  --port <number>     Port for SSE transport (default: 3100)
  -h, --help          Show help
```

### `ton-auth`

Manage authentication.

```
ton-auth login        Open browser to authenticate
ton-auth logout       Clear stored credentials
ton-auth status       Show current plan and usage
```
