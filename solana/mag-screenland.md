---
token: Mag Screenland
ticker: MAG
network: solana
risk_score: 17
status: low
date: 2026-11-03
---

# Mag Screenland (MAG) — Smart Contract Security Analysis | Solana

> **Risk Score: 17/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/mag-screenland-sol)

---

## Audit Summary

The Mag Screenland token is a Token-2022 asset with both mint and freeze authorities successfully revoked, ensuring supply immutability and preventing account freezing. However, the token exhibits a high volume-to-liquidity ratio, suggesting potential wash trading, and holder concentration data is currently unavailable. Third-party risk registry data indicates no adverse flags.

> **Final Recommendation:** Investors should exercise caution regarding the high volume-to-liquidity ratio, which may indicate artificial trading activity. Monitor the token on-chain to verify that no new extensions are initialized if the program allows, though current settings are fixed.

Verify the current holder distribution via block explorers once data becomes available to ensure supply is not overly concentrated among a few wallets. Do not rely solely on the high volume metrics when assessing market demand.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the Token-2022 program with no active transfer hooks or custom extensions. 7.1 Architecture is standard for SPL tokens, and 7.3 Access Control is robust as both mint and freeze… |
| **Governance / Economics** | 8/10 | Low | 7.4 Economic analysis reveals a high volume-to-liquidity ratio of 123.18, which is a strong signal for wash trading. 7.5 Governance is decentralized due to the revoked mint authority, though holder… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable to this mint as it is a standard SPL token. Metadata is immutable, and no balance-mutating authorities exist. The token configuration is static and cannot be altered… |

## Security Findings

_🟠 1 High · ⚪ 5 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume-to-liquidity ratio is 123.18, significantly exceeding the 20x threshold, which is a pattern strongly associated with artificially inflated trade volume.

**Recommendation:** Account for the potential lack of organic demand when calculating entry and exit strategies.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. This assessment covers the main pool, which holds 83% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $71K (DexScreener, all pools). 24h trading volume $3.6M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun (PumpSwap), a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $71K of DEX liquidity across 29 pools. Launch: launched on pump.fun (PumpSwap), under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`AxPzkS...Fo8M`](https://solscan.io/account/AxPzkSJKU3ACqZu7qpq8ov29g4BENZBM4SAZwUUUFo8M) |
| **Network** | Solana |
| **Price** | $0.0004024 |
| **24h Volume** | $3.27M |
| **Liquidity** | $58.3K |
| **Volume / Liquidity** | 56.1× |
| **Token Age** | 2h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 30465 buys / 25159 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/54m3aczla7hk76hsbgrhyysvecaabp7t4j75uxe2esne)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/mag-screenland-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-03*
