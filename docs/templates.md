# Contract Templates

Pre-built, audited contract templates for common TON patterns.

## Available Templates

| Template | Description | Standards | Plan |
|----------|-------------|-----------|------|
| `jetton` | Fungible token (master + wallet) | TEP-74, TEP-89 | Free |
| `nft-collection` | NFT collection + item | TEP-62, TEP-64 | Free |
| `sbt` | Soulbound token collection | TEP-85 | Pro |
| `dao` | DAO governance with proposals & voting | — | Pro |
| `multisig` | Multi-signature wallet (n-of-m) | — | Pro |
| `dex-pool` | DEX liquidity pool (AMM) | — | Pro |

## Usage

```bash
# Scaffold a Jetton
ton-scaffold jetton --name "MyToken" --symbol "MTK"

# Scaffold an NFT collection in FunC
ton-scaffold nft-collection --name "CoolCats" --lang func

# Scaffold a DAO
ton-scaffold dao --name "MyDAO"
```

## What You Get

Each template generates:

- **Contract source files** (Tact or FunC)
- **Deployment script** with configuration
- **Test file** skeleton for TON Sandbox
- **README** with contract-specific documentation

## Template Features

### Jetton (TEP-74)
- Mintable / fixed supply options
- Burn support
- On-chain metadata (TEP-64)
- Owner-controlled minting

### NFT Collection (TEP-62)
- Sequential or random minting
- Royalty support (TEP-66)
- On-chain or off-chain metadata
- Batch minting

### SBT (TEP-85)
- Non-transferable tokens
- Authority-based revocation
- Proof-of-ownership queries

### DAO
- Proposal creation & voting
- Quorum configuration
- Timelock execution
- Token-weighted voting

### Multisig
- Configurable n-of-m signatures
- Order expiration
- Action queuing

### DEX Pool
- Constant-product AMM
- LP token minting/burning
- Fee configuration
- Price oracle helpers
