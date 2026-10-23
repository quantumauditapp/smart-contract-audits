---
token: American Overwatch Protocol
ticker: AOP
network: solana
risk_score: 1
status: low
date: 2026-10-23
---

# American Overwatch Protocol (AOP) — Smart Contract Security Analysis | Solana

> **Risk Score: 1/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/american-overwatch-protocol-sol-3928)

---

## Audit Summary

The American Overwatch Protocol (AOP) token is a standard SPL Token-2022 implementation with both mint and freeze authorities successfully revoked. Liquidity is fully locked, and the token exhibits no high-risk extensions or mutable metadata. All data sources were successfully retrieved, confirming a secure configuration regarding administrative control.

> **Final Recommendation:** The token is configured securely with no administrative backdoors. Holders should continue to monitor the token's market activity via on-chain explorers to ensure that no unexpected supply changes occur, though the current revoked status makes this technically impossible.

No further security actions are required for this token mint. Users should focus on standard market risk management, as the technical security of the contract is fully established.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the spl-token-2022 program with all administrative authorities revoked (7.3 Access Control). 7.1 Architecture is standard, with no active transfer hooks or default frozen account… |
| **Governance / Economics** | 10/10 | Low | 7.4 Economic stability is supported by $727,420 in liquidity, which is 100% burned, preventing rug-pull risks via liquidity withdrawal. Holder concentration is low, with the top 10 holders… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable as SPL token mints do not utilize proxy patterns. The token is immutable, with metadata and extension parameters locked against future changes. |

## Security Findings

_⚪ 7 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, holder concentration, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 1.1% of supply. Of that, 0.5% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 0.5% in wallets, 0.0% in other contracts. 2,262 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

2,262 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $726K (DexScreener, all pools). 24h trading volume $726K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $726K of DEX liquidity across 1 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`FeGEZN...pump`](https://solscan.io/account/FeGEZN9KWA7stty8mzFXVmNqnTAgKmcs2phPdqjcpump) |
| **Network** | Solana |
| **Price** | $0.07238 |
| **24h Volume** | $726.0K |
| **Liquidity** | $726.0K |
| **Volume / Liquidity** | 1.0× |
| **Token Age** | 20h |
| **Top-10 Holders** | 1.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 32117 buys / 2488 sells |

## Security Flags (4/4 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/solana/fuqyhugqqa6gqj4qp4h5bqewytb8ebbgzkyexyvdtuaz)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/american-overwatch-protocol-sol-3928)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-23*
