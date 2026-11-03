---
token: Extended
ticker: XTEN
network: solana
risk_score: 25
status: low
date: 2026-11-03
---

# Extended (XTEN) — Smart Contract Security Analysis | Solana

> **Risk Score: 25/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/extended-sol-a0a0)

---

## Audit Summary

The Extended (XTEN) token utilizes the standard SPL Token program with both mint and freeze authorities successfully revoked. However, the token exhibits high-risk economic indicators, specifically a volume-to-liquidity ratio suggesting wash trading and a lack of locked liquidity. Holder concentration data was unavailable from the queried sources.

> **Final Recommendation:** Investors should exercise extreme caution due to the lack of locked liquidity and the high probability of artificial volume. Monitor the liquidity pool for sudden withdrawals by the creator, as the current lack of locks allows for potential rug-pull scenarios.

Verify the current liquidity status on-chain before executing any trades. Avoid interacting with the token if the liquidity pool size decreases significantly, as this indicates a potential exit by the liquidity provider.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is deployed via the standard spl-token program (7.1 Architecture). Both mint and freeze authorities are revoked, ensuring no further supply inflation or account freezing (7.3 Access… |
| **Governance / Economics** | 5/10 | Medium | Liquidity is currently $162,068, but 0% is locked or burned, posing a significant risk (7.4 Economic). The 24h volume of $53.8M against this liquidity results in a ratio of 332.54, which is a strong… |
| **Upgrades** | 8/10 | Low | The token metadata is immutable, and there are no upgradeable components (7.7 Upgrades). The mint and freeze authorities are permanently revoked, preventing any administrative changes to the token's… |

## Security Findings

_🟠 2 High · 🟡 1 Medium · ⚪ 5 Informational_

### `H-01` — High Volume/Liquidity Ratio  *(Severity: High · Status: Unresolved)*

The volume/liquidity ratio is 332.54, significantly exceeding the 20x threshold, indicating potential wash trading.

**Recommendation:** Exercise caution; high volume may not reflect genuine market demand.


### `H-02` — Pool Liquidity Not Locked  *(Severity: High · Status: Unresolved)*

0% of the pool liquidity is burned or locked, meaning the creator or liquidity provider can withdraw all funds at any time.

**Recommendation:** Monitor the liquidity pool for sudden withdrawals.


### `M-01` — Large Amount of LP Unlocked  *(Severity: Medium · Status: Unresolved)*

Third-party registry signals indicate a large amount of liquidity is currently unlocked and potentially volatile.

**Recommendation:** Verify liquidity provider movements on-chain.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity protection could not be verified  *(Severity: Informational · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 0.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. Solana LP holders are anonymous in the data we read, so who can withdraw the remaining liquidity cannot be verified.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $194K (DexScreener, all pools). 24h trading volume $50.5M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun (PumpSwap), a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $194K of DEX liquidity across 2 pools. Launch: launched on pump.fun (PumpSwap), under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`FKkoKz...SU6p`](https://solscan.io/account/FKkoKzEuujTgmsQKKKDwu6NggehiUiYAhepRgvz2SU6p) |
| **Network** | Solana |
| **Price** | $0.00001415 |
| **24h Volume** | $50.52M |
| **Liquidity** | $194.3K |
| **Volume / Liquidity** | 260.0× |
| **Token Age** | 14h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 46284 buys / 42296 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/7qpeghesetcdf6lqybdngckljyaaszwc9ysryhuvnfhh)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/extended-sol-a0a0)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-03*
