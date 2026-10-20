---
token: ShareX Token
ticker: SHARE
network: bsc
risk_score: 36
status: medium
date: 2026-10-13
---

# ShareX Token (SHARE) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 36/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/sharex-token-bsc)

---

## Audit Summary

The ShareXToken contract is an ERC-20 compliant token with additional features like capping, burning, and permit functionality. The audit found no critical, high, or medium severity vulnerabilities. The contract exhibits a decentralized control structure, as no privileged functions were identified that could unilaterally alter token transfers or critical parameters.

> **Final Recommendation:** The ShareXToken contract demonstrates a robust and decentralized design, with no identified critical security vulnerabilities. It is recommended to ensure that the contract's deployment parameters, such as the initial cap, align with the project's intended tokenomics. Ongoing monitoring of the contract's interactions on the blockchain is always a good practice to detect any unusual activity.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The ShareXToken contract implements the ERC-20 standard, including features like token capping, burning, and permit functionality (7.1 Architecture). Static analysis confirmed the presence of all… |
| **Governance / Economics** | 5/10 | Medium | The contract's economic model includes a capped total supply and burnable tokens, providing clear tokenomics (7.4 Economic). Crucially, the absence of privileged functions means no single entity can… |
| **Upgrades** | 8/10 | Low | The ShareXToken contract is not implemented as a proxy and is therefore not upgradeable (7.7 Upgrades). This eliminates upgrade-related risks such as proxy misconfigurations or malicious upgrade… |

## Security Findings

_⚪ 6 Informational_

### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. What remains: 0.0% in wallets, 100.0% in other contracts. 1 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as ShareX (SHARE), market cap $46M, rank #499. 1 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $22K (DexScreener, all pools). 24h trading volume $10.5M (CoinGecko, all markets, daily snapshot). 24h trading volume $81K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $22K of DEX liquidity across 2 pools. Launch: 20 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 20 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 20 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x5fca...6ac3`](https://bscscan.com/address/0x5fca51aff213bfbeab0b711b93c3374252fd6ac3) |
| **Network** | BNB Chain |
| **Price** | $2.5400 |
| **24h Volume** | $81.3K |
| **Liquidity** | $22.2K |
| **Volume / Liquidity** | 3.7× |
| **Token Age** | 20d |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 166 buys / 122 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x0e0311e7d3c15571656c26a387bf07b930e4982e)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/sharex-token-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-13*
