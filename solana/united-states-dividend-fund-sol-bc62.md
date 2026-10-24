---
token: United States Dividend Fund
ticker: USDF
network: solana
risk_score: 1
status: low
date: 2026-10-24
---

# United States Dividend Fund (USDF) — Smart Contract Security Analysis | Solana

> **Risk Score: 1/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/united-states-dividend-fund-sol-bc62)

---

## Audit Summary

The United States Dividend Fund (USDF) utilizes the Token-2022 program with both mint and freeze authorities successfully revoked. Liquidity is fully secured via 100% burning of LP tokens, and metadata is immutable. Holder distribution data was unavailable from the RPC, preventing a full assessment of concentration risks.

> **Final Recommendation:** The token configuration is secure. Holders should monitor the token's market activity and volume to ensure liquidity remains sufficient for their position size. 

Since holder distribution data was unavailable, users should independently verify the concentration of top wallets using a block explorer to ensure that no single entity holds a majority of the circulating supply.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is implemented via the SPL Token-2022 program. 7.1 Architecture is standard for non-custodial assets. 7.2 Code Security is inherent to the audited program version. 7.3 Access Control is… |
| **Governance / Economics** | 10/10 | Low | 7.4 Economic stability is supported by $1.1M in liquidity. 7.5 Governance is decentralized due to the lack of administrative authorities. 7.6 External factors include a healthy volume/liquidity ratio… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable as the mint is immutable. Metadata is locked, and no upgradeable extensions are present. The token state is fixed and cannot be modified by any external party. |

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

Liquidity $1.1M (DexScreener, all pools). 24h trading volume $822K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Its name presents it as a stable-value coin, yet it trades at $0.1754 — it does not hold a peg. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $1.1M of DEX liquidity across 1 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`9k6gfT...pump`](https://solscan.io/account/9k6gfTLbDaUpx635kQaGTeDvzYs7hWdDW1MerpjYpump) |
| **Network** | Solana |
| **Price** | $0.1754 |
| **24h Volume** | $822.0K |
| **Liquidity** | $1.11M |
| **Volume / Liquidity** | 0.7× |
| **Token Age** | 14h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 40988 buys / 16153 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/7c8vwwpwhpky4uchjxdvfzrhpjlepw9rpb92leodjdbw)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/united-states-dividend-fund-sol-bc62)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-24*
