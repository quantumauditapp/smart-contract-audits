---
token: METACAT
ticker: METACAT
network: solana
risk_score: 27
status: low
date: 2026-10-25
---

# METACAT (METACAT) — Smart Contract Security Analysis | Solana

> **Risk Score: 27/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/metacat-sol)

---

## Audit Summary

METACAT is a Token-2022 asset with fully revoked mint and freeze authorities, providing strong protection against administrative abuse. However, the token exhibits extreme wash-trading indicators and very low liquidity, which poses significant execution risks for holders. Holder concentration data is currently unavailable.

> **Final Recommendation:** Investors should exercise extreme caution due to the high volume/liquidity ratio, which is a strong indicator of wash trading. Before interacting, verify the current liquidity depth on a DEX to ensure that slippage remains within acceptable bounds for your position size.

Monitor the token for any changes in market depth. Since holder concentration data is unavailable, avoid large positions that could be impacted by sudden liquidity shifts or potential whale activity.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the Token-2022 program with no active extensions like transfer hooks or default frozen states. 7.1 Architecture and 7.2 Code Security are standard for SPL mints. 7.3 Access Control… |
| **Governance / Economics** | 5/10 | Medium | 7.4 Economic and 7.5 Governance metrics indicate high risk due to a volume/liquidity ratio of 929.40, suggesting artificial trading activity. Liquidity is extremely low at $4,199, though 100% of the… |
| **Upgrades** | 8/10 | Low | 7.7 Upgrades are not applicable to SPL token mints. Metadata is immutable, and no balance-mutating authorities exist. The token configuration is static and cannot be altered by the original creator. |

## Security Findings

_🟠 2 High · ⚪ 5 Informational_

### `H-01` — Very Low Liquidity  *(Severity: High · Status: Unresolved)*

Total DEX liquidity is $4,199. Slippage will be severe; large positions cannot be exited without significant loss.

**Recommendation:** Account for high slippage in any swap calculation and avoid large position sizes.


### `H-02` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

24-hour volume is 929.40x liquidity — a pattern strongly associated with artificially inflated trade volume.

**Recommendation:** Do not rely on volume metrics as an indicator of genuine market interest or liquidity.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity protection could not be verified  *(Severity: Informational · Status: Acknowledged)*

39.9% of the pool's LP is burned or time-locked. 39.9% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. Solana LP holders are anonymous in the data we read, so who can withdraw the remaining liquidity cannot be verified.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $108K (DexScreener, all pools). 24h trading volume $2.6M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: meme vocabulary in name/ticker (cat); launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $108K of DEX liquidity across 3 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`6uEpcG...pump`](https://solscan.io/account/6uEpcGrKa9S3AupEeDPiGPGvpzgFYxqeLVbXMsJCpump) |
| **Network** | Solana |
| **Price** | $0.0002468 |
| **24h Volume** | $2.58M |
| **Liquidity** | $107.8K |
| **Volume / Liquidity** | 23.9× |
| **Token Age** | 0h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 5366 buys / 4670 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/b98uesp2tvirp2784dcvyxfrfua64fuhpohjmzm1kf5n)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/metacat-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-25*
