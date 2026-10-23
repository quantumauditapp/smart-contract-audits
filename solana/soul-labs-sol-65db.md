---
token: Soul Labs
ticker: SO
network: solana
risk_score: 38
status: medium
date: 2026-10-23
---

# Soul Labs (SO) — Smart Contract Security Analysis | Solana

> **Risk Score: 38/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/soul-labs-sol-65db)

---

## Audit Summary

The Soul Labs token (SO) exhibits significant economic risks due to high holder concentration and suspicious trading patterns. While the mint and freeze authorities are correctly revoked, the lack of locked liquidity and extreme volume-to-liquidity ratio suggest potential market manipulation. Third-party registry data confirms concerns regarding unlocked liquidity and limited provider diversity.

> **Final Recommendation:** Investors should exercise extreme caution due to the lack of locked liquidity and high concentration. Monitor the liquidity pool for sudden withdrawals and verify that the top 10 holders do not initiate coordinated sell-offs.

Before interacting, confirm the current liquidity status on-chain. Avoid large positions that exceed the depth of the liquidity pool to prevent excessive slippage.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The token utilizes the standard spl-token program. 7.1 Architecture and 7.3 Access Control are robust as both mint and freeze authorities are revoked. 7.2 Code Security is standard for the SPL v3… |
| **Governance / Economics** | 4/10 | Medium | 7.4 Economic and 7.5 Governance metrics indicate high risk. The top 10 holders control 81.09% of the supply, creating significant concentration risk. 7.6 External signals show a volume/liquidity… |
| **Upgrades** | 8/10 | Low | 7.7 Upgrades are not applicable to this SPL token mint. 7.8 Operations are stable as metadata is immutable and no balance-mutating authorities exist. The token configuration is fixed. |

## Security Findings

_🟠 3 High · 🟡 1 Medium · ⚪ 6 Informational_

### `H-01` — Holder Concentration > 70%  *(Severity: High · Status: Unresolved)*

The ten largest holders that can sell control 81.09% of the total supply. Coordinated sell-offs by these entities would result in a total collapse of the token price.

**Recommendation:** Monitor the top 10 holder wallets for signs of distribution or coordinated movement.


### `H-02` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume/liquidity ratio is 192.40, significantly exceeding the 20x threshold. This indicates artificial trade volume intended to inflate the token's perceived popularity.

**Recommendation:** Treat volume metrics as unreliable and perform independent analysis of actual market demand.


### `H-03` — Pool Liquidity Not Locked  *(Severity: High · Status: Unresolved)*

0.0% of the pool's liquidity is burned or locked. The liquidity is fully withdrawable, creating a risk that the pool could be drained, leaving holders unable to sell.

**Recommendation:** Verify if the liquidity provider intends to lock the LP tokens to mitigate the risk of a liquidity pull.


### `M-01` — Flagged by Third-Party Registry  *(Severity: Medium · Status: Unresolved)*

Third-party risk registries have flagged this token due to a large amount of unlocked liquidity and a low number of liquidity providers.

**Recommendation:** Review the registry's specific warnings regarding developer history and LP movements.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 91.5% of supply. Of that, 10.5% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 0.3% in wallets, 80.8% in other contracts. 2,617 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

2,617 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity protection could not be verified  *(Severity: Informational · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 0.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. Solana LP holders are anonymous in the data we read, so who can withdraw the remaining liquidity cannot be verified.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $330K (DexScreener, all pools). 24h trading volume $63.1M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun (PumpSwap), a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $330K of DEX liquidity across 2 pools. Launch: launched on pump.fun (PumpSwap), under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`Dwgz5p...tDKV`](https://solscan.io/account/Dwgz5py8Jos3xsKV5frYYEFq1brjB7uX7ZGqq9LZtDKV) |
| **Network** | Solana |
| **Price** | $0.00002067 |
| **24h Volume** | $63.13M |
| **Liquidity** | $330.5K |
| **Volume / Liquidity** | 191.0× |
| **Token Age** | 9h |
| **Top-10 Holders** | 91.5% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 30124 buys / 27290 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/3iquruwxxp5upfwteer7fackaqp6rean4v8ezrrnuahe)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/soul-labs-sol-65db)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-23*
