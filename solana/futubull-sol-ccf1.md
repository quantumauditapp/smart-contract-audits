---
token: 富途牛牛 FUTUBULL
ticker: FUTUBULL
network: solana
risk_score: 27
status: low
date: 2026-10-26
---

# 富途牛牛 FUTUBULL (FUTUBULL) — Smart Contract Security Analysis | Solana

> **Risk Score: 27/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/futubull-sol-ccf1)

---

## Audit Summary

The token utilizes the standard SPL Token program with both mint and freeze authorities successfully revoked. However, the protocol exhibits high risk due to extreme wash-trading signals and the lack of locked liquidity, which allows for potential rug-pull scenarios. Third-party registry data indicates significant concerns regarding holder concentration and LP management.

> **Final Recommendation:** Investors should exercise extreme caution due to the lack of locked liquidity and high wash-trading volume. Monitor the pool's liquidity levels on-chain to detect sudden withdrawals by the pool creator.

Verify the current holder distribution using block explorers to assess the risk of a coordinated sell-off. Do not treat this asset as a long-term store of value given the absence of locked liquidity.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is implemented via the standard SPL Token program (7.1 Architecture). Both mint and freeze authorities are revoked, ensuring no further supply inflation or account freezing (7.3 Access… |
| **Governance / Economics** | 5/10 | Medium | The token exhibits a volume/liquidity ratio of 305.18, indicating severe wash-trading (7.4 Economic). Liquidity is $82,917, but 100% of the pool remains unlocked and withdrawable (7.6 External).… |
| **Upgrades** | 8/10 | Low | The mint is immutable as both authorities are revoked (7.7 Upgrades). Metadata is fixed and cannot be modified (7.8 Operations). No upgrade paths exist for this token program instance. |

## Security Findings

_🟠 2 High · 🟡 1 Medium · ⚪ 5 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume/liquidity ratio is 305.18, which significantly exceeds the 20x threshold, indicating artificially inflated trade volume.

**Recommendation:** Monitor trading activity for signs of automated manipulation.


### `H-02` — Pool Liquidity Not Locked  *(Severity: High · Status: Unresolved)*

0% of the pool liquidity is burned or locked, meaning the entirety of the pool's liquidity can be withdrawn by the creator at any time.

**Recommendation:** Avoid providing liquidity or trading until the pool is locked or burned.


### `M-01` — Flagged High-Risk by Third-Party Registry  *(Severity: Medium · Status: Unresolved)*

An independent third-party risk registry flags this token for high holder concentration and large amounts of unlocked LP.

**Recommendation:** Review the registry's specific warnings regarding developer history and LP movements.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity protection could not be verified  *(Severity: Informational · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 0.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. Solana LP holders are anonymous in the data we read, so who can withdraw the remaining liquidity cannot be verified.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $105K (DexScreener, all pools). 24h trading volume $21.9M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun (PumpSwap), a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $105K of DEX liquidity across 1 pools. Launch: launched on pump.fun (PumpSwap), under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`7xb3EG...BNzE`](https://solscan.io/account/7xb3EGMf4QKud5pT1XmAKDCGXiYvVNZj72AbMFXxBNzE) |
| **Network** | Solana |
| **Price** | $0.0001603 |
| **24h Volume** | $21.86M |
| **Liquidity** | $105.1K |
| **Volume / Liquidity** | 208.1× |
| **Token Age** | 2h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 20837 buys / 14211 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/atakuxx3x3hrueud93yvaihy8r73hek9qiowkmfxdjlx)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/futubull-sol-ccf1)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-26*
