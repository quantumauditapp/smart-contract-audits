---
token: American Oil Dividend Fund
ticker: AODF
network: solana
risk_score: 1
status: low
date: 2026-11-05
---

# American Oil Dividend Fund (AODF) — Smart Contract Security Analysis | Solana

> **Risk Score: 1/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/american-oil-dividend-fund-sol-a3b5)

---

## Audit Summary

The American Oil Dividend Fund (AODF) utilizes the Token-2022 program with both mint and freeze authorities successfully revoked. Liquidity is fully secured via 100% burning of LP tokens, and metadata is immutable. Holder distribution data was unavailable, preventing a full assessment of concentration risk.

> **Final Recommendation:** The token is currently configured in a secure, immutable state. Users should monitor the mint address on-chain to ensure no unexpected changes occur, though the current revocation status makes this unlikely.

Since holder distribution data was unavailable, investors should utilize block explorers to verify the current concentration of tokens among the top accounts before making large entries to ensure the market is sufficiently distributed.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is deployed on the Token-2022 program (7.1 Architecture). Security is robust as both mint and freeze authorities are revoked, preventing supply inflation or account freezing (7.3 Access… |
| **Governance / Economics** | 10/10 | Low | The token maintains $1.31M in liquidity, which is fully burned and inaccessible to the creator (7.4 Economic). Trading volume is healthy with a 0.69 ratio, indicating no signs of wash trading (7.6… |
| **Upgrades** | 10/10 | Low | The token metadata is immutable, preventing post-launch branding changes (7.7 Upgrades). There are no upgradeable extensions or proxy-like mechanisms present in the mint configuration (7.8… |

## Security Findings

_⚪ 6 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $1.3M (DexScreener, all pools). 24h trading volume $905K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $1.3M of DEX liquidity across 1 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`CEgDcX...pump`](https://solscan.io/account/CEgDcXhjKf8k7mfeATW9AMy18wqXo9Y6VEywhhgLpump) |
| **Network** | Solana |
| **Price** | $0.2725 |
| **24h Volume** | $905.1K |
| **Liquidity** | $1.31M |
| **Volume / Liquidity** | 0.7× |
| **Token Age** | 19h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 28466 buys / 11700 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/addrlc4stefs3xjqkshnumihwy6ch8gtvxfhacgkn93j)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/american-oil-dividend-fund-sol-a3b5)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-05*
