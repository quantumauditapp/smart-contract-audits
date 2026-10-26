---
token: Mubarakah
ticker: MUBARAKAH
network: bsc
risk_score: 3
status: low
date: 2026-09-22
---

# Mubarakah (MUBARAKAH) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 3/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/mubarakah-bsc)

---

## Audit Summary

The audited contract is an ERC20-compliant token with custom transfer restriction modes. It utilizes the Ownable pattern for administrative control. A critical vulnerability was identified in the `setMode` function, which permanently disables the ability to re-enable transfer restrictions once the token is set to 'normal' mode. Additionally, the token starts in a restricted state, requiring manual owner action to enable transfers.

> **Final Recommendation:** It is critical to address the `setMode` function's logic to allow the owner to re-enable transfer restrictions if needed, providing essential emergency control. Consider implementing a multi-signature wallet for ownership to reduce single points of failure. Ensure clear documentation and operational procedures are in place for setting the initial token mode and managing ownership.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The contract implements a standard ERC20 token with custom transfer modes (7.1 Architecture). The `_beforeTokenTransfer` hook correctly enforces these modes. The `ERC20` base contract uses… |
| **Governance / Economics** | 8/10 | Low | The token's economic model relies on centralized control by an `owner` address (7.5 Governance). The initial state `MODE_TRANSFER_RESTRICTED` means the token is untransferable until the owner… |
| **Upgrades** | 10/10 | Low | The contract is not designed with upgradeability patterns (e.7.7 Upgrades). This means its logic is immutable after deployment. While not a direct upgrade vulnerability, the permanent nature of the… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Locked** | 99.8% — GoPlus SafeToken Locker |
| **Top-1 Unlocked Holder** | 0.2% |

## Security Findings

_🟡 3 Medium_

### `M-01` — Centralized Control by Owner  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract inherits `Ownable`, granting a single external address (the `owner`) exclusive control over critical functions such as `setMode` and `transferOwnership`. This centralization introduces a single point of failure; if the owner's private key is compromised, lost, or becomes inaccessible, the protocol's functionality could be severely impacted or halted.

**Recommendation:** Consider migrating ownership to a multi-signature wallet (e.g., Gnosis Safe) or a decentralized autonomous organization (DAO) to distribute control and reduce the risk associated with a single point of failure. If a multi-sig is not feasible, ensure the owner's private key is secured with the highest industry standards.


### `M-02` — Irreversible Loss of Transfer Control Mechanism  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `setMode` function contains a conditional check `if (_mode != MODE_NORMAL)` before allowing the mode to be updated. This means that once the token's `_mode` is set to `MODE_NORMAL` (0), the condition `_mode != MODE_NORMAL` becomes false, and the `_mode` variable can never be changed again. This permanently removes the owner's ability to re-enable transfer restrictions (e.g., `MODE_TRANSFER_RESTRICTED` or `MODE_TRANSFER_CONTROLLED`) in case of an emergency, exploit, or necessary protocol upgrade, leading to a critical loss of control over token transfers.

**Recommendation:** Remove the conditional check `if (_mode != MODE_NORMAL)` from the `setMode` function to allow the owner to freely change the token's mode between all defined states at any time. This ensures that emergency controls remain available throughout the token's lifecycle.


### `M-03` — Initial Transfer Restriction Requires Manual Activation  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The token's constructor initializes `_mode` to `MODE_TRANSFER_RESTRICTED` (1). In this mode, all transfers are reverted with the message 'Token: Transfer is restricted'. This means the token is non-functional for transfers immediately after deployment until the owner explicitly calls `setMode(MODE_NORMAL)`. If the owner fails to perform this action, or if the owner's key is compromised before this action, the tokens could remain permanently locked and untransferable.

**Recommendation:** Ensure robust operational procedures are in place for the initial deployment and activation of the token. Consider adding a time-lock or a multi-signature requirement for the initial `setMode` call to `MODE_NORMAL` to prevent hasty or unauthorized activation. Clearly document this critical post-deployment step.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x3199...8a9a`](https://bscscan.com/address/0x3199a64bc8aabdfd9a3937a346cc59c3d81d8a9a) |
| **Network** | BNB Chain |
| **Price** | $0.000623 |
| **24h Volume** | $282.5K |
| **Liquidity** | $96.6K |
| **Volume / Liquidity** | 2.9× |
| **Token Age** | 1y |
| **Top-10 Holders** | 86.5% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1356 buys / 1514 sells |

## Security Flags (5/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0xacb622435b634e75b61473be6f839c46e36bd754)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/mubarakah-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-22*
