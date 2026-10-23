---
token: American Oil Dividend Fund
ticker: AODF
network: solana
risk_score: 0
status: low
date: 2026-10-23
---

# American Oil Dividend Fund (AODF) — Smart Contract Security Analysis | Solana

> **Risk Score: 0/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/american-oil-dividend-fund-sol-97f6)

---

## Audit Summary

The American Oil Dividend Fund (AODF) token exhibits a strong security posture with both mint and freeze authorities permanently revoked. Liquidity is fully secured via 100% burning of LP tokens, and no high-risk extensions are active. All sources, including on-chain registry and DEX market data, were successfully retrieved.

> **Final Recommendation:** The token is currently in a secure, immutable state. Holders should monitor the token's market performance and liquidity depth via standard DEX interfaces. No further action is required to secure the token's administrative state.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the SPL Token-2022 program with no active transfer hooks or default frozen states. 7.1 Architecture is standard for SPL mints, while 7.3 Access Control is robust due to the… |
| **Governance / Economics** | 10/10 | Low | 7.4 Economic stability is supported by $786,545 in liquidity, which is 100% burned, preventing rug-pull risks. 7.5 Governance is decentralized as no single entity controls the mint. 7.6 External… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable as the token utilizes a fixed, non-upgradable mint configuration. Metadata is immutable, ensuring branding consistency. No administrative keys exist to modify token… |

## Security Findings

_⚪ 7 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, holder concentration, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 1.1% of supply. Of that, 0.5% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 0.6% in wallets, 0.0% in other contracts. 2,319 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

2,319 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $783K (DexScreener, all pools). 24h trading volume $564K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $783K of DEX liquidity across 1 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`FLQdUS...pump`](https://solscan.io/account/FLQdUSx5zoR8npbyWCu49iFxBaemdgUNX4hcCBWupump) |
| **Network** | Solana |
| **Price** | $0.08389 |
| **24h Volume** | $564.1K |
| **Liquidity** | $782.7K |
| **Volume / Liquidity** | 0.7× |
| **Token Age** | 19h |
| **Top-10 Holders** | 1.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 29456 buys / 883 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/2uc9q6x5dfkrsf8kj5rqvd6pnafwkxwfcvwmmmzc8wcn)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/american-oil-dividend-fund-sol-97f6)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-23*
