---
token: Catori
ticker: CATORI
network: solana
risk_score: 38
status: medium
date: 2026-11-02
---

# Catori (CATORI) — Smart Contract Security Analysis | Solana

> **Risk Score: 38/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/catori-sol)

---

## Audit Summary

The Catori token is a standard SPL-2022 mint with both mint and freeze authorities successfully revoked. The primary risks identified are low liquidity and a high volume-to-liquidity ratio, which suggests potential wash trading. All third-party registry data was successfully retrieved and no adverse flags were reported.

> **Final Recommendation:** Investors should exercise caution due to the low liquidity, which may result in significant slippage during trades. Monitor the token's trading activity to ensure that volume is organic rather than artificially inflated.

Verify the current supply and authority status using a block explorer to confirm that no changes have occurred since this audit. Avoid large market orders that could be impacted by the low liquidity depth.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The token utilizes the SPL-2022 program (7.1 Architecture). Access control is secure as both mint and freeze authorities are revoked (7.3 Access Control). The token does not utilize transfer hooks or… |
| **Governance / Economics** | 5/10 | Medium | Holder concentration is low, with the top 10 holders controlling 7.07% of the supply (7.5 Governance). Liquidity is $8,838, which is below the $10,000 threshold (7.4 Economic). The… |
| **Upgrades** | 8/10 | Low | The token metadata is immutable, preventing post-launch branding changes (7.7 Upgrades). There are no upgradeable components or proxy patterns present (7.8 Operations). The token state is fixed and… |

## Security Findings

_🟠 1 High · 🟡 2 Medium · ⚪ 5 Informational_

### `H-01` — Very Low Liquidity  *(Severity: High · Status: Unresolved)*

Total DEX liquidity is $8,838. Slippage will be severe; large positions cannot be exited without significant loss.

**Recommendation:** Account for the fee in any swap calculation.


### `M-01` — Wash Trading Signal  *(Severity: Medium · Status: Unresolved)*

24-hour volume is 110.21x liquidity — a pattern strongly associated with artificially inflated trade volume.

**Recommendation:** Monitor trading patterns for signs of artificial volume before executing large trades.


### `QA-MARKET` — The market for this token  *(Severity: Medium · Status: Acknowledged)*

Liquidity $9K (DexScreener, all pools). 24h trading volume $974K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 94.5% of supply. Of that, 3.6% locked, 83.8% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 7.1% in wallets, 0.0% in other contracts. 181 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

181 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: meme vocabulary in name/ticker (cat); launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $9K of DEX liquidity across 1 pools. Launch: launched on pump.fun, 3 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 3 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 3 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`FDwCos...pump`](https://solscan.io/account/FDwCosavNvMiFB812ajJp3gG7eZ9c4bpgcnY6fDQpump) |
| **Network** | Solana |
| **Price** | $0.00001389 |
| **24h Volume** | $974.0K |
| **Liquidity** | $8.7K |
| **Volume / Liquidity** | 112.0× |
| **Token Age** | 3d |
| **Top-10 Holders** | 94.5% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 13948 buys / 7178 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/6af3tkqifdacbc5xmztl4i2zwbqlukp6e1famed4t5uq)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/catori-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-02*
