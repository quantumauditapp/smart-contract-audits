---
token: French Fry Security
ticker: FRY
network: solana
risk_score: 38
status: medium
date: 2026-10-30
---

# French Fry Security (FRY) — Smart Contract Security Analysis | Solana

> **Risk Score: 38/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/french-fry-security-sol)

---

## Audit Summary

The token exhibits significant economic risks, specifically high holder concentration and extreme wash-trading signals. While the mint and freeze authorities are correctly revoked, the lack of locked liquidity and high volume-to-liquidity ratio suggest a volatile environment. Third-party registry data confirms the presence of large amounts of unlocked liquidity.

> **Final Recommendation:** Investors should exercise extreme caution due to the high concentration of supply and the lack of locked liquidity. Monitor the top 10 holder wallets for potential sell-offs and verify liquidity movements on-chain before committing capital.

Verify the current liquidity pool status via block explorers to ensure no sudden withdrawals occur. Avoid trading during periods of extreme volume-to-liquidity spikes, as these are often indicative of artificial market activity.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The token utilizes the standard SPL Token program (v3). 7.1 Architecture and 7.2 Code Security are standard for this program. 7.3 Access Control is robust as both mint and freeze authorities are… |
| **Governance / Economics** | 4/10 | Medium | 7.4 Economic and 7.5 Governance risks are elevated due to 81.29% concentration among the top 10 holders. 7.6 External signals indicate a volume/liquidity ratio of 197.02, suggesting significant wash… |
| **Upgrades** | 8/10 | Low | 7.7 Upgrades are not applicable as this is a standard SPL token. Metadata is immutable, preventing branding changes. No upgradeable extensions are present. |

## Security Findings

_🟠 3 High · 🟡 1 Medium · ⚪ 6 Informational_

### `H-01` — Holder Concentration > 70%  *(Severity: High · Status: Unresolved)*

The ten largest holders that can sell hold 81.29% of the supply. Coordinated sell-off would crash price; single-whale dumps are common in this range.

**Recommendation:** Monitor top holder wallets for divestment patterns.


### `H-02` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

24-hour volume is 197.02x liquidity, a pattern strongly associated with artificially inflated trade volume.

**Recommendation:** Exercise caution; volume may not represent organic market demand.


### `H-03` — Pool Liquidity Not Locked  *(Severity: High · Status: Unresolved)*

0.0% of the pool's liquidity is burned or locked; the remaining liquidity is not protected from withdrawal.

**Recommendation:** Treat the pool as removable until liquidity is burned or locked.


### `M-01` — Flagged by Third-Party Registry  *(Severity: Medium · Status: Unresolved)*

Third-party risk registry signals indicate a large amount of LP is unlocked and there is a low amount of LP providers.

**Recommendation:** Review registry data for specific developer history or LP movement alerts.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 89.4% of supply. Of that, 8.1% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 1.3% in wallets, 80.0% in other contracts. 2,590 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

2,590 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity protection could not be verified  *(Severity: Informational · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 0.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. Solana LP holders are anonymous in the data we read, so who can withdraw the remaining liquidity cannot be verified.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $171K (DexScreener, all pools). 24h trading volume $32.8M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun (PumpSwap), a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $171K of DEX liquidity across 2 pools. Launch: launched on pump.fun (PumpSwap), under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`3eb8Ep...tNAB`](https://solscan.io/account/3eb8Ep4R6yiAPtAAYMLLzyswLYdFanzEcd6d3jURtNAB) |
| **Network** | Solana |
| **Price** | $0.00001041 |
| **24h Volume** | $32.81M |
| **Liquidity** | $170.8K |
| **Volume / Liquidity** | 192.1× |
| **Token Age** | 9h |
| **Top-10 Holders** | 89.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 27872 buys / 25359 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/3soqfy5wghuqkl5qvybswghx4h9uuv7kzxderebkx5l3)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/french-fry-security-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-30*
