---
token: 富途牛牛 FUTUBULL
ticker: FUTUBULL
network: solana
risk_score: 29
status: low
date: 2026-10-25
---

# 富途牛牛 FUTUBULL (FUTUBULL) — Smart Contract Security Analysis | Solana

> **Risk Score: 29/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/futubull-sol)

---

## Audit Summary

The assessment identified an elevated volume-to-liquidity ratio of 321.96 and completely unlocked DEX liquidity (0.0% burned or locked), signaling significant economic risk. Conversely, core technical access controls are secure as both mint and freeze authorities are permanently revoked. Token holder concentration data from chain-native RPC was unavailable at the time of evaluation.

> **Final Recommendation:** Continuously track the liquidity pool token accounts using an on-chain explorer to verify whether LP tokens are transferred into verifiable lock contracts or burn addresses. Avoid executing large market orders that rely on the reported trading volume until liquidity commitments are formalized.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The mint operates under the standard SPL Token program with 6 decimals and an initial raw supply of 999,998,043,955,259. Access control is strictly finalized on-chain with both the mint authority and… |
| **Governance / Economics** | 5/10 | Medium | DEX liquidity stands at $95,802 against an outsized 24-hour volume of $30,843,972, creating an abnormal ratio of 321.96 in a pair created today (age 0 days). Exactly 0.0% of the pool's liquidity is… |
| **Upgrades** | 8/10 | Low | The token features no administrative update vector as both mint and freeze capabilities are permanently revoked. Off-chain registries confirm metadata mutability is disabled, preventing changes to… |

## Security Findings

_🟠 1 High · 🟡 1 Medium · ⚪ 5 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

24-hour volume is 321.96x liquidity — a pattern strongly associated with artificially inflated trade volume.

**Recommendation:** Exercise caution and do not rely on reported trading volume as an indicator of genuine market depth or organic interest.


### `M-01` — Pool Liquidity Not Locked  *(Severity: Medium · Status: Unresolved)*

Only 0.0% of the pool's liquidity is burned or locked; the rest can be withdrawn by whoever holds it (Solana LP holders are anonymous in the data we read, so who can withdraw the remaining liquidity cannot be verified).

**Recommendation:** Track LP token accounts on-chain and treat DEX liquidity as removable until proof of permanent locking or burning is verified.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity protection could not be verified  *(Severity: Informational · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 0.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. Solana LP holders are anonymous in the data we read, so who can withdraw the remaining liquidity cannot be verified.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $82K (DexScreener, all pools). 24h trading volume $27.2M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun (PumpSwap), a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $82K of DEX liquidity across 1 pools. Launch: launched on pump.fun (PumpSwap), under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`GgJAd2...HDT9`](https://solscan.io/account/GgJAd2C5NSLa5vkCo7e75GFfXMhkGjNJt7nJ9DcmHDT9) |
| **Network** | Solana |
| **Price** | $0.0001882 |
| **24h Volume** | $27.20M |
| **Liquidity** | $81.5K |
| **Volume / Liquidity** | 333.8× |
| **Token Age** | 3h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 26201 buys / 17527 sells |

## Security Flags (3/4 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/solana/gxs5kbjabn5w8vsvqm1la59avynmvqtpqp31upa2ru3p)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/futubull-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-25*
