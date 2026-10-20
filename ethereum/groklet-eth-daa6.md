---
token: Groklet
ticker: GROKLET
network: ethereum
risk_score: 28
status: low
date: 2026-10-20
---

# Groklet (GROKLET) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 28/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/groklet-eth-daa6)

---

## Audit Summary

The contract is a standard ERC-20 token with additional tax, limit, and trading control features. Ownership has been renounced, meaning all privileged functions are now permanently disabled. The code is functional and follows standard patterns for this type of token, though it contains minor arithmetic and authorization design patterns that are typical for this category.

> **Final Recommendation:** The contract is currently in a 'locked' state due to the renounced ownership. No further action is required for the current deployment as the administrative functions are inaccessible. 

For future deployments, ensure that all arithmetic operations involving percentages are performed using multiplication before division to maintain precision and prevent rounding errors.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The architecture follows a standard ERC-20 implementation with integrated tax and limit logic. 7.1 Architecture is straightforward, utilizing standard OpenZeppelin-like patterns. 7.2 Code Security… |
| **Governance / Economics** | 10/10 | Low | 7.4 Economic parameters are fixed as ownership is renounced. 7.5 Governance is non-existent as no further changes can be made to the contract state. 7.6 External dependencies are limited to standard… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not supported as the contract is not a proxy. 7.8 Operations are stable since the contract is immutable and ownership is renounced. |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Null Address |

## Security Findings

_🟡 1 Medium · 🟢 1 Low · ⚪ 9 Informational_

### `CD-02` — Usage of tx.origin for Authorization  *(Severity: Medium · Status: Unresolved)*

The contract uses tx.origin for certain logic, which can be vulnerable to phishing attacks if a user is tricked into interacting with a malicious contract.

**Recommendation:** Use msg.sender instead of tx.origin for all authorization and rule checks.


### `CD-01` — Rounding Loss in Fee Calculation  *(Severity: Low · Status: Unresolved)*

The _transfer function performs division before multiplication, which can lead to minor precision loss in fee calculations.

**Recommendation:** Refactor arithmetic to perform multiplication before division.


### `CP-05` — Dormant Administrative Switches  *(Severity: Informational · Status: Unresolved)*

Functions like enableTrading and removeLimits control transfer rules. Because ownership is renounced, these functions are permanently disabled and cannot be triggered.

**Recommendation:** No action required as the contract is effectively immutable.


### `CP-07` — Dormant Fee Configuration  *(Severity: Informational · Status: Unresolved)*

Functions updateSellFees and updateBuyFees allow changing tax rates. These are now inaccessible due to renounced ownership.

**Recommendation:** No action required.


### `CP-08` — Dormant Limit Configuration  *(Severity: Informational · Status: Unresolved)*

Functions controlling transaction and wallet limits are now permanently locked.

**Recommendation:** No action required.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The holder list from the security indexer adds up to 113.3% of supply, so it does not describe real balances. That happens with rebasing and reflection tokens, whose balances change without transfers, and with contracts that report balances they do not hold. Concentration is unknown and priced as an unknown — neither a whale nor safe.

**Recommendation:** Check the largest holders on the block explorer, which reads current balances.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

638 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $77K (DexScreener, all pools). 24h trading volume $655K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $77K of DEX liquidity across 1 pools. Launch: 1 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 1 day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 1 day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x5acd...647f`](https://etherscan.io/address/0x5acd735f50c16c7618fb0af48b2a2e0e682a647f) |
| **Network** | Ethereum |
| **Price** | $0.0008889 |
| **24h Volume** | $655.5K |
| **Liquidity** | $76.8K |
| **Volume / Liquidity** | 8.5× |
| **Token Age** | 1d |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 413 buys / 179 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x7e5e5198b8773339243ae0f905e0a770180ff1de)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/groklet-eth-daa6)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-20*
