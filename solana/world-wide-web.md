---
token: world wide web
ticker: WWW
network: solana
risk_score: 1
status: low
date: 2026-10-06
---

# world wide web (WWW) — Smart Contract Security Analysis | Solana

> **Risk Score: 1/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/world-wide-web-sol)

---

## Audit Summary

This audit of the 'world wide web' SPL Token Mint found no critical or high-severity issues based on the provided on-chain facts and external security signals. The mint and freeze authorities are revoked, and all pool liquidity is permanently burned. Third-party risk registry data reported no adverse flags, and chain-native RPC data for holder distribution was unavailable.

> **Final Recommendation:** No immediate critical actions are required given the current state of the token. Holders should verify on-chain that the mint and freeze authorities remain revoked to ensure supply and transfer immutability. Monitor the token's liquidity and trading volume for any significant changes that could impact market stability, although current liquidity is locked. No specific on-chain verification steps are needed regarding mutable features, as all relevant authorities are revoked or features are disabled.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The 'world wide web' token is an SPL Token-2022 mint with a total supply of 992,345,156.298489 tokens and 6 decimals. Both the mint authority and freeze authority have been revoked, preventing… |
| **Governance / Economics** | 10/10 | Low | Holder concentration is low, with the top 10 holders that can sell accounting for only 11.91% of the supply. The token has a liquidity of $78,474 USD, and 100.0% of the pool's LP tokens are burned… |
| **Upgrades** | 10/10 | Low | The mint authority and freeze authority are both revoked, indicating that the token's supply and transferability parameters are immutable. No Token-2022 extensions like transfer hooks or default… |

## Security Findings

_⚪ 7 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, holder concentration, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 29.8% of supply. Of that, 1.8% locked, 16.1% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 11.9% in wallets, 0.0% in other contracts. 6,949 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

6,949 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. This assessment covers the main pool, which holds 74% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $101K (DexScreener, all pools). 24h trading volume $537K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun (PumpSwap), a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $101K of DEX liquidity across 13 pools. Launch: launched on pump.fun (PumpSwap), 4 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 4 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 4 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`GAwhcp...9S9H`](https://solscan.io/account/GAwhcphCqCv5bKHmCiN4VDdNWfbXJL4npmkc8L3Q9S9H) |
| **Network** | Solana |
| **Price** | $0.000301 |
| **24h Volume** | $441.7K |
| **Liquidity** | $74.9K |
| **Volume / Liquidity** | 5.9× |
| **Token Age** | 4d |
| **Top-10 Holders** | 29.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 3124 buys / 2733 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/cr469kh7ocptqk5yademjvpbwx1dixxlioopfjn23jsg)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/world-wide-web-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-06*
