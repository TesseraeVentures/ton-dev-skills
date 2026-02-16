# API — MCP Tool Schemas

Reference for all tools exposed by the MCP server. Each tool accepts a JSON input and returns a JSON result.

---

## `ton_audit`

Run a security audit on contract source code.

**Input:**
```json
{
  "source": "string — contract source code",
  "language": "func | tact | tolk (auto-detected if omitted)",
  "severity": "info | low | medium | high (default: info)",
  "categories": ["string — category names to check (default: all)"]
}
```

**Output:**
```json
{
  "findings": [
    {
      "id": "string — rule ID",
      "severity": "high | medium | low | info",
      "category": "string",
      "message": "string — human-readable description",
      "line": "number",
      "column": "number",
      "suggestion": "string — recommended fix"
    }
  ],
  "summary": {
    "high": "number",
    "medium": "number",
    "low": "number",
    "info": "number",
    "rulesChecked": "number"
  }
}
```

---

## `ton_migrate`

Migrate a Solidity contract to TON-native.

**Input:**
```json
{
  "source": "string — Solidity source code",
  "targetLanguage": "tact | func (default: tact)",
  "dryRun": "boolean (default: false)"
}
```

**Output:**
```json
{
  "files": [
    {
      "path": "string — relative file path",
      "content": "string — generated source code"
    }
  ],
  "report": {
    "sourceType": "string — detected EVM standard (e.g., ERC-20)",
    "targetType": "string — TON equivalent (e.g., Jetton)",
    "translations": ["string — patterns translated"],
    "removals": ["string — EVM patterns removed"],
    "tepCompliance": ["string — TEPs satisfied"]
  },
  "audit": "object — ton_audit output for generated code"
}
```

---

## `ton_scaffold`

Generate a contract from template.

**Input:**
```json
{
  "template": "jetton | nft-collection | sbt | dao | multisig | dex-pool",
  "name": "string — contract/token name",
  "symbol": "string — token symbol (for jetton)",
  "language": "tact | func (default: tact)"
}
```

**Output:**
```json
{
  "files": [
    {
      "path": "string",
      "content": "string"
    }
  ]
}
```

---

## `ton_compile`

Compile a contract to BOC.

**Input:**
```json
{
  "source": "string — contract source code",
  "language": "func | tact | tolk"
}
```

**Output:**
```json
{
  "boc": "string — base64-encoded BOC",
  "hash": "string — code cell hash"
}
```

---

## `ton_tep_check`

Check TEP compliance.

**Input:**
```json
{
  "source": "string — contract source code",
  "language": "func | tact | tolk",
  "teps": ["string — TEP numbers to check, e.g., '74', '62' (default: auto-detect)"]
}
```

**Output:**
```json
{
  "results": [
    {
      "tep": "string — TEP number",
      "name": "string — TEP name",
      "compliant": "boolean",
      "issues": ["string — non-compliance details"]
    }
  ]
}
```

---

## `ton_fetch_contract`

Fetch on-chain contract code by address.

**Input:**
```json
{
  "address": "string — TON address",
  "network": "mainnet | testnet (default: mainnet)"
}
```

**Output:**
```json
{
  "address": "string",
  "boc": "string — base64-encoded BOC",
  "hash": "string — code cell hash",
  "balance": "string — nanoTON"
}
```

---

## `ton_disassemble`

Disassemble a BOC to TVM instructions.

**Input:**
```json
{
  "boc": "string — base64-encoded BOC"
}
```

**Output:**
```json
{
  "instructions": ["string — human-readable TVM instructions"]
}
```

---

## `ton_test_gen`

Generate test cases for a contract.

**Input:**
```json
{
  "source": "string — contract source code",
  "language": "func | tact | tolk",
  "framework": "sandbox | jest (default: sandbox)"
}
```

**Output:**
```json
{
  "testFile": "string — generated test source code",
  "testCount": "number — number of test cases generated"
}
```
