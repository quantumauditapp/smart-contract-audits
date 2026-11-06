---
token: bracket
ticker: BRACKET
network: solana
risk_score: 36
status: medium
date: 2026-11-06
---

# bracket (BRACKET) — Smart Contract Security Analysis | Solana

> **Risk Score: 36/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/bracket-sol)

---

## Audit Summary

The bracket token (EFWotn2UtV2c5QXMMHbSzmyrkU7wnfj7VpkNQGr1wk1z) utilizes the Token-2022 program with both mint and freeze authorities successfully revoked. While the liquidity is fully burned, the token exhibits a high volume-to-liquidity ratio, suggesting potential wash trading. Holder concentration data is currently unavailable.

> **Final Recommendation:** Investors should exercise caution due to the low liquidity and high volume-to-liquidity ratio, which are indicative of artificial trading activity. Before interacting, verify the current market depth on a DEX to ensure that the slippage remains within acceptable parameters for your trade size.

Monitor the token's price action and volume patterns over time to determine if the high activity is organic. Since holder concentration data is unavailable, avoid large positions that could be impacted by sudden liquidity shifts or whale activity.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The token is implemented via the Token-2022 program, ensuring modern extension compatibility. 7.1 Architecture and 7.2 Code Security are standard for this program. 7.3 Access Control is robust, as… |
| **Governance / Economics** | 5/10 | Medium | 7.4 Economic stability is challenged by a very low liquidity pool of $9,290, which may cause significant slippage. 7.6 External market data indicates a volume/liquidity ratio of 135.45, which is a… |
| **Upgrades** | 8/10 | Low | 7.7 Upgrades are not applicable as the mint is a standard SPL token. Metadata is immutable, and no balance-mutating authorities are present. The configuration is static and cannot be altered by the… |

## Security Findings

_🟠 1 High · 🟡 2 Medium · ⚪ 4 Informational_

### `H-01` — Very Low Liquidity  *(Severity: High · Status: Unresolved)*

Total DEX liquidity is $9,290. Slippage will be severe; large positions cannot be exited without significant loss.

**Recommendation:** Account for the liquidity constraints in any swap calculation.


### `M-01` — Wash Trading Signal  *(Severity: Medium · Status: Unresolved)*

24-hour volume is 135.45x liquidity — a pattern strongly associated with artificially inflated trade volume.

**Recommendation:** Exercise caution; high volume relative to liquidity often indicates non-organic trading activity.


### `QA-MARKET` — The market for this token  *(Severity: Medium · Status: Acknowledged)*

Liquidity $9K (DexScreener, all pools). 24h trading volume $1.3M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun (PumpSwap), a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $9K of DEX liquidity across 30 pools. Launch: launched on pump.fun (PumpSwap), under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`EFWotn...wk1z`](https://solscan.io/account/EFWotn2UtV2c5QXMMHbSzmyrkU7wnfj7VpkNQGr1wk1z) |
| **Network** | Solana |
| **Price** | $0.00001315 |
| **24h Volume** | $1.26M |
| **Liquidity** | $9.1K |
| **Volume / Liquidity** | 138.3× |
| **Token Age** | 11h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 17952 buys / 13659 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/5wdfxkkvaxl6rn9jcfzdgtgibszdb7qgzwqqytbc3srk)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/bracket-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-06*
