---
token: PVE
ticker: PVE
network: ethereum
risk_score: 38
status: medium
date: 2026-10-25
---

# PVE (PVE) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 38/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/pve-eth-01ec)

---

## Audit Summary

The contract is a standard ERC-20 token with additional features for trading control, fees, and anti-whale mechanisms. Ownership has been successfully renounced, meaning the privileged administrative functions are now permanently disabled. The code is functional and follows standard patterns for this type of token, though minor arithmetic and architectural patterns were identified.

> **Final Recommendation:** The contract is safe for interaction as the owner has renounced control, effectively locking the parameters. Users should be aware that the fixed logic includes transfer fees and potential wallet limits that cannot be changed in the future.

For future deployments, consider using msg.sender instead of tx.origin to improve security against phishing attacks and avoid division-before-multiplication patterns to ensure precision in fee calculations.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The architecture follows a standard ERC-20 implementation with integrated liquidity management. 7.1 Architecture and 7.2 Code Security are generally sound, though the use of tx.origin for logic is… |
| **Governance / Economics** | 8/10 | Low | 7.4 Economic and 7.5 Governance aspects are currently static. Since ownership is renounced, no further changes to fees, limits, or blacklists can be enacted by any party. The economic model is fixed… |
| **Upgrades** | 8/10 | Low | 7.7 Upgrades are not supported as this is a non-proxy contract. 7.8 Operations are stable because the contract logic is immutable. No upgrade path exists, ensuring the current logic remains permanent. |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Null Address |

## Security Findings

_🟡 1 Medium · 🟢 1 Low · ⚪ 9 Informational_

### `CD-02` — Use of tx.origin for Authorization  *(Severity: Medium · Status: Unresolved)*

The contract uses tx.origin to determine certain rules. This is a security risk because it can be exploited by malicious contracts to bypass authorization checks if a user is tricked into interacting with them.

**Recommendation:** Replace all instances of tx.origin with msg.sender to ensure that the immediate caller is the one being authorized.


### `CD-01` — Potential Precision Loss in Calculations  *(Severity: Low · Status: Unresolved)*

The _transfer function performs division before multiplication, which can lead to rounding errors and slight inaccuracies in fee calculations.

**Recommendation:** Reorder operations to perform multiplication before division to maintain higher precision.


### `CP-05` — Dormant Administrative Switches  *(Severity: Informational · Status: Unresolved)*

The contract contains switches (e.g., enableTrading, removeLimits) that control token transfer behavior. Because ownership is renounced, these functions are now inaccessible, rendering these controls permanently fixed in their current state.

**Recommendation:** No action required as the renouncement provides a security guarantee that these settings cannot be altered.


### `CP-07` — Fixed Transfer Fees  *(Severity: Informational · Status: Unresolved)*

The contract includes functions to update buy and sell fees. Since ownership is renounced, these fees are now permanently set to their current values and cannot be adjusted by any party.

**Recommendation:** None required; the immutability of fees is a feature of the current state.


### `CP-08` — Fixed Transaction and Wallet Limits  *(Severity: Informational · Status: Unresolved)*

The contract defines maximum transaction and wallet limits. These limits are now immutable due to the renouncement of ownership, preventing any future adjustments to the token's distribution rules.

**Recommendation:** None required.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The holder list from the security indexer adds up to 156.6% of supply, so it does not describe real balances. That happens with rebasing and reflection tokens, whose balances change without transfers, and with contracts that report balances they do not hold. Concentration is unknown and priced as an unknown — neither a whale nor safe.

**Recommendation:** Check the largest holders on the block explorer, which reads current balances.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

140 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $22K (DexScreener, all pools). 24h trading volume $56K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $22K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x4fae...6578`](https://etherscan.io/address/0x4fae6afd6074f0f39a9fec54061d267fd3776578) |
| **Network** | Ethereum |
| **Price** | $0.00005259 |
| **24h Volume** | $55.8K |
| **Liquidity** | $22.4K |
| **Volume / Liquidity** | 2.5× |
| **Token Age** | 8h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 190 buys / 183 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x388c4bb7d6419f22c76806cfaba72ef59b77cf1c)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/pve-eth-01ec)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-25*
