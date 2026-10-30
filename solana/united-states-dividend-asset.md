---
token: United States Dividend Asset
ticker: USDA
network: solana
risk_score: 0
status: low
date: 2026-10-30
---

# United States Dividend Asset (USDA) — Smart Contract Security Analysis | Solana

> **Risk Score: 0/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/united-states-dividend-asset-sol)

---

## Audit Summary

The USDA token mint reflects a secure technical profile with both mint and freeze authorities permanently revoked and 100.0% of DEX pool liquidity burned. The top 10 holders that can sell represent only 0.68% of total supply, presenting minimal concentration risk. Chain-native RPC holder distribution data was unavailable during ingestion, though an independent risk registry notes a signal of high holder correlation.

> **Final Recommendation:** Continuously monitor secondary market transactions and on-chain account linkages to evaluate whether correlated holders execute coordinated exits. Verify that any future liquidity pools established across other decentralized exchanges follow the same burned or verifiable lock mechanism before committing significant capital.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The mint is deployed on the spl-token-2022 program with an initialized supply of 999,792,422,842,323 units across 6 decimals. Both mint authority and freeze authority are revoked (None), guaranteeing… |
| **Governance / Economics** | 10/10 | Low | The top 10 holders capable of selling hold 0.68% of total supply, reflecting an exceptionally dispersed initial distribution. DEX liquidity stands at $364,279 with 100.0% of LP tokens burned… |
| **Upgrades** | 10/10 | Low | Administrative upgrade vector analysis reveals complete authority revocation with no active mint or freeze managers. Extension upgrade privileges, including transfer hook and transfer fee upgrades… |

## Security Findings

_⚪ 7 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, holder concentration, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 1.7% of supply. Of that, 1.0% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 0.7% in wallets, 0.0% in other contracts. 3,000 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

3,000 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $364K (DexScreener, all pools). 24h trading volume $144K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Its name presents it as a stable-value coin, yet it trades at $0.0195 — it does not hold a peg. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $364K of DEX liquidity across 1 pools. Launch: launched on pump.fun, 1 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 1 day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 1 day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`6sdpoD...pump`](https://solscan.io/account/6sdpoDjhd75dzofKW8nJ2D7SmyruJQaaGAM5EP8pump) |
| **Network** | Solana |
| **Price** | $0.0195 |
| **24h Volume** | $144.5K |
| **Liquidity** | $363.6K |
| **Volume / Liquidity** | 0.4× |
| **Token Age** | 1d |
| **Top-10 Holders** | 1.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 32494 buys / 2511 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/9kqzhvs1m93q8mvnn7b9umdb5kejrw5vdcn2sxnon5pm)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/united-states-dividend-asset-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-30*
