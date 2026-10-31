---
token: FUN
ticker: FUN
network: solana
risk_score: 21
status: low
date: 2026-10-31
---

# FUN (FUN) — Smart Contract Security Analysis | Solana

> **Risk Score: 21/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/fun-sol)

---

## Audit Summary

The FUN token utilizes the Token-2022 program with both mint and freeze authorities successfully revoked, ensuring supply immutability and preventing account freezing. However, the token exhibits a high volume-to-liquidity ratio of 35.58, which is a strong indicator of wash trading. Holder concentration data is unavailable, and while liquidity is fully burned, the high trading activity relative to liquidity poses a risk to price stability.

> **Final Recommendation:** Investors should exercise caution regarding the high volume-to-liquidity ratio, which suggests artificial trading activity. Monitor the token's price stability and liquidity depth before executing large trades.

Verify the current supply and authority status using a block explorer to confirm that the mint and freeze authorities remain revoked. Since holder concentration data is unavailable, avoid large positions that could be subject to significant slippage or sudden price impact.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is deployed on the Token-2022 program (7.1 Architecture). Both mint and freeze authorities are revoked, ensuring no further supply inflation or account confiscation (7.3 Access Control).… |
| **Governance / Economics** | 7/10 | Low | Liquidity is fully burned, preventing withdrawal by the creator (7.4 Economic). However, the volume-to-liquidity ratio of 35.58 suggests significant wash trading activity (7.6 External). Holder… |
| **Upgrades** | 10/10 | Low | The mint is immutable as the mint authority is revoked (7.7 Upgrades). Metadata is non-mutable, ensuring branding consistency (7.2 Code Security). There are no upgradeable components or proxy… |

## Security Findings

_🟠 1 High · ⚪ 5 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume-to-liquidity ratio is 35.58, exceeding the 20x threshold, which is a pattern strongly associated with artificially inflated trade volume.

**Recommendation:** Monitor trading activity for signs of manipulation and account for potential liquidity gaps during high-volatility events.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $23K (DexScreener, all pools). 24h trading volume $733K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $23K of DEX liquidity across 2 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`FDSG65...pump`](https://solscan.io/account/FDSG65a94jA3mdC47VPikD5WARCJN5ffSgot3TfHpump) |
| **Network** | Solana |
| **Price** | $0.00008153 |
| **24h Volume** | $598.5K |
| **Liquidity** | $23.0K |
| **Volume / Liquidity** | 26.0× |
| **Token Age** | 6h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 9405 buys / 6672 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/f8avz2mq1dff2t2kgswsin3cwbq2eywwoerz4fabwxqm)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/fun-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-31*
