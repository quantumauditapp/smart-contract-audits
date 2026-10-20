---
token: DE NEO AGENT
ticker: DNA
network: bsc
risk_score: 26
status: low
date: 2026-10-18
---

# DE NEO AGENT (DNA) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 26/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/de-neo-agent-bsc)

---

## Audit Summary

The DeNeoAgent contract is an ERC-20 token with standard functionalities including burning and permit extensions. The audit found no critical, high, medium, or low-severity vulnerabilities. The contract appears well-structured and adheres to common ERC-20 standards.

> **Final Recommendation:** It is recommended that token holders and integrators thoroughly understand the standard ERC-20 functionalities and the implications of ERC20Burnable and ERC20Permit. While the contract appears robust, users should always exercise caution and verify interactions with external platforms. Developers should ensure all external integrations correctly handle ERC-20 token transfers and approvals.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The DeNeoAgent contract implements the ERC-20 standard, including ERC20Burnable and ERC20Permit functionalities, enhancing usability and flexibility (7.1 Architecture). All standard ERC-20 functions… |
| **Governance / Economics** | 6/10 | Medium | The DeNeoAgent contract functions as a standard ERC-20 token without complex economic models or governance mechanisms (7.4 Economic, 7.5 Governance). Its value and stability are primarily dependent… |
| **Upgrades** | 8/10 | Low | The DeNeoAgent contract is not designed as an upgradeable proxy (7.7 Upgrades). Its logic is immutable once deployed, which simplifies its operational model but means any future changes would require… |

## Security Findings

_⚪ 6 Informational_

### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. What remains: 0.0% in wallets, 100.0% in other contracts. 4 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as NeoSoul (DNA), market cap $37M, rank #565. 4 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $201K (DexScreener, all pools). 24h trading volume $45.3M (CoinGecko, all markets, daily snapshot). 24h trading volume $24.3M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $201K of DEX liquidity across 13 pools. Launch: 2 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 2 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 2 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xa991...cf7b`](https://bscscan.com/address/0xa991f61940095aea0724ef54077223b048c5cf7b) |
| **Network** | BNB Chain |
| **Price** | $0.282 |
| **24h Volume** | $1.38M |
| **Liquidity** | $143.8K |
| **Volume / Liquidity** | 9.6× |
| **Token Age** | 2d |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 3651 buys / 3986 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x005db8721ef9dadccf8b99f151b1763e8c58ba61)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/de-neo-agent-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-18*
