---
token: GTA6
ticker: GTA 6 COIN
network: solana
risk_score: 1
status: low
date: 2026-11-07
---

# GTA6 (GTA 6 COIN) — Smart Contract Security Analysis | Solana

> **Risk Score: 1/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/gta6-sol-5336)

---

## Audit Summary

The GTA6 token utilizes the Token-2022 program with both mint and freeze authorities successfully revoked. While the liquidity is fully burned, the token exhibits signs of wash trading and low liquidity, which may impact price stability. Holder concentration data is currently unavailable from on-chain sources.

> **Final Recommendation:** Investors should exercise caution due to the extremely low liquidity, which will cause significant slippage on even small trade sizes. Monitor the token's volume-to-liquidity ratio to avoid participating in potentially artificial trading environments.

Verify the current supply on-chain to ensure it matches expectations, as the mint authority is revoked and no further tokens can be created. Do not rely on third-party registry flags regarding holder concentration until more granular on-chain data becomes available.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is initialized on the Token-2022 program. 7.1 Architecture is standard for SPL mints. 7.3 Access Control is robust as both mint and freeze authorities are revoked. 7.2 Code Security is… |
| **Governance / Economics** | 10/10 | Low | 7.4 Economic indicators show high risk due to $2,499 in liquidity, triggering a 'Very Low Liquidity' finding. 7.6 External data indicates a volume/liquidity ratio of 43.51, suggesting wash trading.… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable to this SPL mint. Metadata is immutable, and there are no upgradable extensions configured. The token state is fixed and cannot be altered by the original deployer. |

## Security Findings

_🟠 2 High · ⚪ 5 Informational_

### `H-01` — Very Low Liquidity  *(Severity: High · Status: Unresolved)*

Total DEX liquidity is $2,499. Slippage will be severe; large positions cannot be exited without significant loss.

**Recommendation:** Ensure trade sizes are significantly smaller than the available liquidity pool to minimize price impact.


### `H-02` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

24-hour volume is 43.51x liquidity — a pattern strongly associated with artificially inflated trade volume.

**Recommendation:** Exercise caution as high volume relative to liquidity often indicates non-organic market activity.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $58K (DexScreener, all pools). 24h trading volume $65K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $58K of DEX liquidity across 1 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`9yhSHq...pump`](https://solscan.io/account/9yhSHqFw3sSTu8m9DgY4YceJyDdNQAXEsphCw5xdpump) |
| **Network** | Solana |
| **Price** | $0.0005645 |
| **24h Volume** | $65.2K |
| **Liquidity** | $58.2K |
| **Volume / Liquidity** | 1.1× |
| **Token Age** | 1h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 19505 buys / 18682 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/athvvej8hazc7bzoccp69rhtethvtco9ms9nme3vgexk)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/gta6-sol-5336)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-07*
