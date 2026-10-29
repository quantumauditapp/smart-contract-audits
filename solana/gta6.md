---
token: GTA6
ticker: GTA 6 COIN
network: solana
risk_score: 4
status: low
date: 2026-10-29
---

# GTA6 (GTA 6 COIN) — Smart Contract Security Analysis | Solana

> **Risk Score: 4/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/gta6-sol)

---

## Audit Summary

The GTA6 token mint is configured with both mint and freeze authorities revoked, preventing unauthorized supply inflation or account freezing. Third-party risk registry data indicates no adverse flags, and liquidity is sufficient for current trading volumes. The primary risk is the lack of confirmed liquidity locking, which should be verified by users.

> **Final Recommendation:** Investors should verify the liquidity pool status on-chain to confirm if assets are locked or burned, as this information was not available during the audit. Monitor the top holder wallets periodically to ensure no significant concentration shifts occur that could impact market stability.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the standard SPL Token program (v3). 7.1 Architecture and 7.3 Access Control are robust as both mint and freeze authorities are revoked. 7.2 Code Security is inherent to the… |
| **Governance / Economics** | 8/10 | Low | 7.4 Economic and 7.5 Governance metrics show healthy distribution with the top 10 holders controlling 17.97% of supply. 7.6 External data confirms $144,267 in liquidity with a low volume/liquidity… |
| **Upgrades** | 9/10 | Low | 7.7 Upgrades are not applicable as SPL tokens do not support proxy-based logic updates. Metadata is immutable, ensuring branding consistency. The token configuration is finalized and cannot be… |

## Security Findings

_🟡 1 Medium · ⚪ 4 Informational_

### `M-01` — Pool Liquidity Not Locked  *(Severity: Medium · Status: Unresolved)*

The fact block does not confirm that the pool's liquidity is burned or locked. Without verification, the pool creator may retain the ability to withdraw liquidity.

**Recommendation:** Verify the liquidity pool's lock status via a block explorer or liquidity locker platform to ensure funds are protected.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 25.2% of supply. Of that, 7.2% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 18.0% in wallets, 0.0% in other contracts. 11,810 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

11,810 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $146K (DexScreener, all pools). 24h trading volume $33K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $146K of DEX liquidity across 14 pools. Launch: launched on pump.fun, 638 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`EaxAUc...pump`](https://solscan.io/account/EaxAUcXxNnVwcqm2BBocbows7D1XVY2Q63V38NEypump) |
| **Network** | Solana |
| **Price** | $0.0009843 |
| **24h Volume** | $32.1K |
| **Liquidity** | $140.1K |
| **Volume / Liquidity** | 0.2× |
| **Token Age** | 1y |
| **Top-10 Holders** | 25.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 261 buys / 281 sells |

## Security Flags (3/4 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ⚠️ Unknown |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/solana/9kgswjrkczs3ebukvbkbgdwj8bwtdwzzqxkufdhaps2a)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/gta6-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-29*
