---
token: Charizard
ticker: CHARIZARD
network: solana
risk_score: 0
status: low
date: 2026-10-21
---

# Charizard (CHARIZARD) — Smart Contract Security Analysis | Solana

> **Risk Score: 0/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/charizard-sol)

---

## Audit Summary

The Charizard token is a standard SPL Token-2022 implementation with both mint and freeze authorities successfully revoked. Liquidity is fully secured via a 100% burn of LP tokens, mitigating risks of rug pulls. Third-party registries have flagged concentration concerns, though on-chain data confirms the majority of supply is held in DEX reserves.

> **Final Recommendation:** Investors should monitor the top 10 holder wallets for potential coordinated sell-offs, as concentration remains a factor despite the secure liquidity structure. No further on-chain action is required to secure the token mint itself.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the SPL Token-2022 program with no active transfer hooks or custom extensions. 7.1 Architecture is standard, and 7.3 Access Control is robust as both mint and freeze authorities… |
| **Governance / Economics** | 10/10 | Low | 7.4 Economic health is supported by $96,415 in liquidity, which is 100% burned. 7.5 Governance is decentralized as no single entity holds minting power. 7.6 External signals indicate high holder… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable as the token utilizes a fixed program standard. Metadata is immutable, and no balance-mutating authorities exist. The token configuration is finalized and cannot be… |

## Security Findings

_🟡 1 Medium · ⚪ 6 Informational_

### `M-01` — Holder Concentration  *(Severity: Medium · Status: Unresolved)*

The ten largest holders that can sell control 18.57% of the total supply. While this is below the 50% threshold for high risk, it represents a significant portion of the circulating supply held by a small number of addresses.

**Recommendation:** Monitor the top 10 holder addresses for large, sudden transfers to DEX pools to anticipate potential price volatility.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 82.5% of supply. Of that, 63.9% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 18.6% in wallets, 0.0% in other contracts. 623 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

623 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $90K (DexScreener, all pools). 24h trading volume $271K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $90K of DEX liquidity across 25 pools. Launch: launched on pump.fun, 2 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 2 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 2 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`D9rASp...pump`](https://solscan.io/account/D9rASpRWPyMYQGVLQLEN4S4Cy8fYE7fP8au9Gy7Upump) |
| **Network** | Solana |
| **Price** | $0.0001051 |
| **24h Volume** | $261.2K |
| **Liquidity** | $89.4K |
| **Volume / Liquidity** | 2.9× |
| **Token Age** | 2d |
| **Top-10 Holders** | 82.5% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2293 buys / 1720 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/5jmkohrtreunyxkpfjr2ycr4cayxtytmh1d3te6x2pxs)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/charizard-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-21*
