---
token: saluteface
ticker: SALUTEFACE
network: solana
risk_score: 40
status: medium
date: 2026-10-20
---

# saluteface (SALUTEFACE) — Smart Contract Security Analysis | Solana

> **Risk Score: 40/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/saluteface-sol)

---

## Audit Summary

The mint presents critical economic risks driven by a low pool liquidity of $8,074 coupled with an abnormal 24-hour trading volume of $973,462, reflecting severe wash-trading signals and slippage exposure. Administrative controls are fully decentralised as both mint and freeze capabilities are permanently revoked, and 100% of the initial liquidity pool is burned. Note that chain-native RPC holder distribution data was unavailable during fact collection.

> **Final Recommendation:** Traders should configure conservative slippage tolerances and restrict trade sizing to prevent high price impact against the thin pool reserve. Ongoing monitoring should verify that DEX pool balances are maintained and track organic order flow via on-chain block explorers rather than trusting aggregate DEX volume statistics.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The asset operates on the spl-token-2022 standard program with an initialized fixed supply of 966,891,394.663014 units across 6 decimals. Both mint and freeze authorities are revoked (set to None)… |
| **Governance / Economics** | 5/10 | Medium | Top 10 sell-capable holders control 21.85% of the circulating supply, while the DEX pool reserve accounts for 58.38%. The pool's LP tokens are 100.0% burned, guaranteeing that market liquidity cannot… |
| **Upgrades** | 8/10 | Low | All core administrative authorities have been permanently extinguished with no upgrade paths available. The Token-2022 program configuration contains no transfer fee upgrade authority or transfer… |

## Security Findings

_🟠 2 High · 🟡 1 Medium · ⚪ 5 Informational_

### `H-01` — Very Low Liquidity  *(Severity: High · Status: Unresolved)*

Total DEX liquidity is $8,074. Slippage will be severe; large positions cannot be exited without significant loss.

**Recommendation:** Verify current pool depth before executing orders and restrict transaction sizes to avoid massive price impact.


### `H-02` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

24-hour volume is 120.57x liquidity — a pattern strongly associated with artificially inflated trade volume.

**Recommendation:** Disregard 24-hour reported volume metrics as a signal of authentic user activity or organic market demand.


### `QA-MARKET` — The market for this token  *(Severity: Medium · Status: Acknowledged)*

Liquidity $8K (DexScreener, all pools). 24h trading volume $974K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 80.2% of supply. Of that, 58.4% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 21.9% in wallets, 0.0% in other contracts. 514 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

514 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $8K of DEX liquidity across 3 pools. Launch: launched on pump.fun, 4 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 4 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 4 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`7avWDo...pump`](https://solscan.io/account/7avWDoV6xH2Fw4zeqnEAULeQtEvayeqM11uxPzMupump) |
| **Network** | Solana |
| **Price** | $0.00001013 |
| **24h Volume** | $973.7K |
| **Liquidity** | $8.2K |
| **Volume / Liquidity** | 118.6× |
| **Token Age** | 4d |
| **Top-10 Holders** | 80.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 6195 buys / 5197 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/cn6rdudwhwbeoqqisuntuxjmt4xmcu7hrw8xz34fjahm)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/saluteface-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-20*
