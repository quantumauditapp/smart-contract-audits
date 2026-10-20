---
token: Rip Kim Jong-Un
ticker: KIM
network: solana
risk_score: 13
status: low
date: 2026-10-19
---

# Rip Kim Jong-Un (KIM) — Smart Contract Security Analysis | Solana

> **Risk Score: 13/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/rip-kim-jong-un-sol)

---

## Audit Summary

The mint exhibits strong structural parameters with revoked mint and freeze authorities alongside 100.0% burned pool liquidity. A High-severity risk was identified from DEX market data showing an anomalous volume-to-liquidity ratio of 50.55 ($3,119,688 volume against $61,712 liquidity), indicative of wash trading. Chain-native RPC holder distribution data was unavailable during analysis.

> **Final Recommendation:** Rely strictly on the visible pool depth of $61,712 when modeling price impact, ignoring 24-hour trading volume which shows severe inflation signals. Perform an independent check of the largest token accounts via a secondary RPC provider or block explorer to verify holder concentration prior to executing transactions.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token operates on the spl-token-2022 program with an initialized raw supply of 964,435,037,498,133 across 6 decimals. Both mint and freeze authorities are permanently revoked, preventing… |
| **Governance / Economics** | 8/10 | Low | DEX liquidity stands at $61,712, with 100.0% of the pool's LP tokens burned, completely removing the creator withdrawal risk. However, 24-hour volume reached $3,119,688, yielding an extreme… |
| **Upgrades** | 10/10 | Low | All core administrative authorities are revoked, meaning no owner key can alter minting privileges or freeze assets. Metaplex metadata mutability is set to false, ensuring token branding, name, and… |

## Security Findings

_🟠 1 High · ⚪ 5 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

24-hour volume is 50.55x liquidity — a pattern strongly associated with artificially inflated trade volume.

**Recommendation:** Exercise caution when interpreting trading metrics; assume reported transaction activity does not reflect organic market demand.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. This assessment covers the main pool, which holds 59% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $123K (DexScreener, all pools). 24h trading volume $3.4M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $123K of DEX liquidity across 29 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`ESABfJ...pump`](https://solscan.io/account/ESABfJpt9cocXgWX7HF8WwSXrcv785oyaA8imwojpump) |
| **Network** | Solana |
| **Price** | $0.0005958 |
| **24h Volume** | $3.02M |
| **Liquidity** | $72.0K |
| **Volume / Liquidity** | 41.9× |
| **Token Age** | 23h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 29517 buys / 22232 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/2sa5714m6bst4zdpxs5trfppeaz1pcamdyhggatfrazw)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/rip-kim-jong-un-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-19*
