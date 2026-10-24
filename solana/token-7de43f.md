---
token: かぼす
ticker: かぼす
network: solana
risk_score: 36
status: medium
date: 2026-10-24
---

# かぼす (かぼす) — Smart Contract Security Analysis | Solana

> **Risk Score: 36/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/token-7de43f-sol)

---

## Audit Summary

The token utilizes the Token-2022 program with both mint and freeze authorities successfully revoked. The primary risks identified are low liquidity and a high volume-to-liquidity ratio, which may indicate artificial trading activity. All third-party registry data was available and reported no adverse flags.

> **Final Recommendation:** Investors should exercise caution regarding the low liquidity and high volume-to-liquidity ratio, which may lead to significant slippage during trades. Monitor the token's market depth on decentralized exchanges before executing large orders.

Verify the current supply and holder distribution via a block explorer to ensure no unexpected concentration changes occur. No further administrative actions are required as the mint and freeze authorities are already revoked.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The token is implemented via the Token-2022 program. 7.1 Architecture and 7.3 Access Control are robust as both mint and freeze authorities are revoked. 7.2 Code Security is standard for SPL mints… |
| **Governance / Economics** | 5/10 | Medium | 7.4 Economic analysis reveals a liquidity of $9,477, which falls below the $10,000 threshold. 7.5 Governance is decentralized as the top 10 holders control only 19.47% of the supply. However, the… |
| **Upgrades** | 8/10 | Low | 7.7 Upgrades are not applicable to this SPL mint as it lacks proxy patterns. Metadata is immutable, and extension-specific authorities (transfer fee, hook) are not present or are not upgradable. The… |

## Security Findings

_🟠 2 High · 🟡 1 Medium · ⚪ 5 Informational_

### `H-01` — Very Low Liquidity  *(Severity: High · Status: Unresolved)*

Total DEX liquidity is $9,477. Slippage will be severe; large positions cannot be exited without significant loss.

**Recommendation:** Account for the liquidity constraints in any swap calculation.


### `H-02` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

24-hour volume is 26.43x liquidity — a pattern strongly associated with artificially inflated trade volume.

**Recommendation:** Exercise caution as trading volume may not reflect genuine market demand.


### `QA-MARKET` — The market for this token  *(Severity: Medium · Status: Acknowledged)*

Liquidity $8K (DexScreener, all pools). 24h trading volume $336K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 44.9% of supply. Of that, 25.5% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 19.5% in wallets, 0.0% in other contracts. 187 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

187 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $8K of DEX liquidity across 8 pools. Launch: launched on pump.fun, 2 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 2 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 2 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`2mrT8h...pump`](https://solscan.io/account/2mrT8hizpKykdYUHN2uYcNkxGbGnZSumvXQMuwSkpump) |
| **Network** | Solana |
| **Price** | $0.00001241 |
| **24h Volume** | $247.0K |
| **Liquidity** | $8.1K |
| **Volume / Liquidity** | 30.6× |
| **Token Age** | 2d |
| **Top-10 Holders** | 44.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 7515 buys / 3601 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/hmv4xq6a9b8o1ugfdc5z8bp1syhfjmfnc53uxygclrwe)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/token-7de43f-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-24*
