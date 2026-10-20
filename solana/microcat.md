---
token: Microcat
ticker: MICRO
network: solana
risk_score: 15
status: low
date: 2026-10-04
---

# Microcat (MICRO) — Smart Contract Security Analysis | Solana

> **Risk Score: 15/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/microcat-sol)

---

## Audit Summary

The Microcat (MICRO) token mint has revoked both mint and freeze authorities, indicating a fixed supply and no ability to freeze accounts. However, a significant risk is identified in the holder concentration, with the top 10 holders that can sell controlling 100.00% of the supply, posing a high risk of market manipulation. All available security signals from on-chain and third-party registries indicate no adverse flags, and liquidity is fully burned. Third-party registry data was available and reported no adverse flags.

> **Final Recommendation:** Given the extreme holder concentration, it is crucial to monitor the activity of the top 10 holders that can sell for any large movements that could impact market stability. While the liquidity is robustly locked, the concentrated ownership presents a significant risk. Investors should exercise extreme caution and consider the potential for sudden price volatility due to large holder actions before acquiring this token.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The Microcat (MICRO) token operates on the standard `spl-token` program. Its mint authority is revoked, ensuring no new tokens can be minted, fixing the total supply at 954,748,350,727,522 raw units… |
| **Governance / Economics** | 9/10 | Low | A critical economic risk is the extreme holder concentration, with the top 10 holders that can sell controlling 100.00% of the total supply, including 16.65% in wallets and 83.35% in program… |
| **Upgrades** | 10/10 | Low | The token's mint authority and freeze authority are both revoked, meaning the token's core parameters related to supply and account freezing cannot be changed. The metadata is also immutable… |

## Security Findings

_🟠 1 High · ⚪ 6 Informational_

### `H-01` — Holder Concentration > 70%  *(Severity: High · Status: Unresolved)*

The ten largest holders that can sell hold 100.00% of supply. Coordinated sell-off would crash price; single-whale dumps are common in this range.

**Recommendation:** Monitor the activity of the top holders for any large movements that could impact market stability. Be aware of the potential for significant price volatility due to concentrated ownership.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. What remains: 16.7% in wallets, 83.4% in other contracts. 14 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Microcat (MICRO), rank #4321. 14 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. This assessment covers the main pool, which holds 84% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $64K (DexScreener, all pools). 24h trading volume $294K (CoinGecko, all markets, daily snapshot). 24h trading volume $267K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: meme vocabulary in name/ticker (cat); launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $64K of DEX liquidity across 6 pools. Launch: launched on pump.fun, 3 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 3 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 3 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`DvNcJZ...pump`](https://solscan.io/account/DvNcJZTiSMD1RBCtZ2J31mh7s42CVCwrzGapv1Lypump) |
| **Network** | Solana |
| **Price** | $0.000224 |
| **24h Volume** | $242.0K |
| **Liquidity** | $53.8K |
| **Volume / Liquidity** | 4.5× |
| **Token Age** | 3d |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1726 buys / 1880 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/mnnen34cbujj7pvfdb2pn7whgrvcmzctej4baguixob)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/microcat-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-04*
