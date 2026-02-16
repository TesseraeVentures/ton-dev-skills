# Migration Report

**Source:** `MyToken.sol` (ERC-20)
**Target:** Jetton Master + Jetton Wallet (Tact)
**Generated:** 2026-02-16T12:00:00Z

---

## Source Analysis

| Property | Value |
|----------|-------|
| Standard | ERC-20 |
| Name | MyToken |
| Symbol | MTK |
| Decimals | 18 |
| Mintable | Yes (owner only) |
| Burnable | Yes |
| Pausable | No |

## Generated Files

| File | Description |
|------|-------------|
| `my-token-master.tact` | Jetton master contract (TEP-74) |
| `my-token-wallet.tact` | Jetton wallet contract (TEP-89) |

## Pattern Translations

| EVM Pattern | TON Equivalent | Notes |
|-------------|----------------|-------|
| `mapping(address => uint256) balances` | Per-wallet contract (Jetton Wallet) | Balances stored in individual wallet contracts |
| `transfer(to, amount)` | `internal_transfer` op + `transfer_notification` | Two-step: debit sender wallet → credit receiver wallet |
| `mint(to, amount)` | `mint` op on master → deploys/credits wallet | Master sends internal mint to wallet contract |
| `burn(amount)` | `burn` op on wallet → `burn_notification` to master | Wallet burns and notifies master to update supply |
| `totalSupply` | `get_jetton_data()` get-method | On-chain queryable |
| `balanceOf(address)` | `get_wallet_data()` on wallet contract | Query individual wallet contracts |

## Removed Patterns

These EVM patterns have no equivalent on TON's actor model:

| Pattern | Reason |
|---------|--------|
| `approve / transferFrom / allowance` | Not applicable — TON uses direct wallet-to-wallet transfers |
| `event Transfer(...)` | Replaced by `transfer_notification` messages |
| `event Approval(...)` | No approval mechanism on TON |

## TEP Compliance

| TEP | Name | Status |
|-----|------|--------|
| TEP-74 | Fungible Tokens (Jettons) | ✅ Compliant |
| TEP-89 | Discoverable Jettons Wallets | ✅ Compliant |
| TEP-64 | Token Data Standard | ✅ Compliant |

## Security Audit (Generated Code)

Automatic audit of generated contracts:

| Severity | Count |
|----------|-------|
| 🔴 High | 0 |
| 🟡 Medium | 0 |
| 🔵 Low | 0 |
| 🟢 Info | 1 |

**Info:** Consider adding metadata URI for off-chain metadata support.
