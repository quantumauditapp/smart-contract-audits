---
token: Soul Labs
ticker: SO
network: solana
risk_score: 28
status: low
date: 2026-10-21
---

# Soul Labs (SO) — Smart Contract Security Analysis | Solana

> **Risk Score: 28/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/soul-labs-sol-6b29)

---

## Audit Summary

The Soul Labs token (SO) demonstrates a high risk profile primarily due to the lack of locked liquidity and suspicious trading patterns. While the mint and freeze authorities are correctly revoked, the absence of locked liquidity allows for potential removal of pool funds. Third-party registry data indicates a high volume of unlocked LP tokens, and the volume-to-liquidity ratio suggests potential wash trading.

> **Final Recommendation:** Investors should exercise extreme caution due to the lack of locked liquidity. Monitor the liquidity pool for sudden withdrawals, as the current structure allows the pool creator to remove all funds at any time. 

Verify the token's market activity independently, as the high volume-to-liquidity ratio is a strong indicator of artificial trading. Do not treat this asset as a long-term store of value until liquidity is provably locked or burned.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the standard spl-token program. 7.1 Architecture is standard for SPL mints. 7.3 Access Control is robust, as both mint and freeze authorities are revoked. 7.8 Operations are stable… |
| **Governance / Economics** | 5/10 | Medium | 7.4 Economic and 7.6 External factors indicate significant risk. Liquidity is $386,623, but 100% remains unlocked, creating a risk of sudden withdrawal. 7.5 Governance is impacted by the lack of… |
| **Upgrades** | 8/10 | Low | 7.7 Upgrades are not applicable as SPL token mints do not support proxy-based logic updates. Metadata is immutable, and no transfer hooks or balance-mutating extensions are active. |

## Security Findings

_🟠 2 High · 🟡 1 Medium · ⚪ 5 Informational_

### `H-01` — Pool Liquidity Not Locked  *(Severity: High · Status: Unresolved)*

0.0% of the pool's liquidity is burned or locked; the remaining liquidity can be withdrawn by the pool creator.

**Recommendation:** Lock or burn the liquidity tokens to prevent the pool creator from withdrawing all funds.


### `H-02` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume/liquidity ratio is 101.13, which is significantly above the 20x threshold, indicating potential artificial trade volume.

**Recommendation:** Exercise caution; high volume-to-liquidity ratios often indicate manipulated market activity.


### `M-01` — High-Risk Liquidity Distribution  *(Severity: Medium · Status: Unresolved)*

Third-party risk registry flags a large amount of unlocked LP tokens and a low number of liquidity providers.

**Recommendation:** Monitor the liquidity pool for large, sudden exits by the primary providers.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity protection could not be verified  *(Severity: Informational · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 0.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. Solana LP holders are anonymous in the data we read, so who can withdraw the remaining liquidity cannot be verified.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $372K (DexScreener, all pools). 24h trading volume $36.0M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun (PumpSwap), a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $372K of DEX liquidity across 2 pools. Launch: launched on pump.fun (PumpSwap), under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`DGNE5Z...PpPE`](https://solscan.io/account/DGNE5ZJfVRDysfrHetZXPdjWP3boHxRmGpTQ2JxSPpPE) |
| **Network** | Solana |
| **Price** | $0.00001596 |
| **24h Volume** | $35.96M |
| **Liquidity** | $372.2K |
| **Volume / Liquidity** | 96.6× |
| **Token Age** | 5h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 17567 buys / 15767 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/hj2dfju4rzsmyda86wqoolq3jgfda2uuezmvcemcqx8g)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/soul-labs-sol-6b29)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-21*
