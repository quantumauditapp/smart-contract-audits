---
token: Extended
ticker: XTEN
network: solana
risk_score: 29
status: low
date: 2026-11-05
---

# Extended (XTEN) — Smart Contract Security Analysis | Solana

> **Risk Score: 29/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/extended-sol-4e46)

---

## Audit Summary

The Extended (XTEN) token utilizes the standard SPL Token program with both mint and freeze authorities successfully revoked. However, the token exhibits high-risk economic indicators, specifically a high volume-to-liquidity ratio suggesting potential wash trading and a lack of locked liquidity. Holder distribution data was unavailable for this assessment.

> **Final Recommendation:** Investors should exercise extreme caution due to the lack of locked liquidity and the high probability of artificial volume. Monitor the pool liquidity status on-chain to ensure it is not withdrawn by the creator.

Verify the current liquidity provider status via block explorers to determine if the pool creator is actively managing the unlocked funds. Avoid large positions until liquidity is demonstrably locked or burned.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is deployed on the standard SPL Token program (7.1 Architecture). Both mint and freeze authorities are revoked, ensuring no further supply inflation or account freezing (7.3 Access… |
| **Governance / Economics** | 5/10 | Medium | The token exhibits a volume/liquidity ratio of 269.83, significantly exceeding the 20x threshold for suspicious trading activity (7.4 Economic). 100% of the pool liquidity is currently unlocked and… |
| **Upgrades** | 8/10 | Low | The token metadata is immutable, preventing post-launch branding changes (7.7 Upgrades). There are no upgradeable components or proxy patterns inherent to this SPL token mint (7.8 Operations). |

## Security Findings

_🟠 2 High · 🟡 1 Medium · ⚪ 5 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume/liquidity ratio is 269.83, which is significantly higher than the 20x threshold, indicating potential artificial trade volume.

**Recommendation:** Monitor trading activity for organic volume before committing capital.


### `H-02` — Pool Liquidity Not Locked  *(Severity: High · Status: Unresolved)*

0% of the pool liquidity is burned or locked, meaning the entirety of the liquidity can be withdrawn by the pool creator.

**Recommendation:** Verify if the liquidity provider intends to lock the LP tokens to protect against sudden liquidity removal.


### `M-01` — High-Risk LP Status  *(Severity: Medium · Status: Unresolved)*

Third-party risk registry signals indicate a large amount of unlocked LP and a low number of liquidity providers.

**Recommendation:** Exercise caution as the pool is susceptible to sudden withdrawal and low depth.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity protection could not be verified  *(Severity: Informational · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 0.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. Solana LP holders are anonymous in the data we read, so who can withdraw the remaining liquidity cannot be verified.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $192K (DexScreener, all pools). 24h trading volume $40.1M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun (PumpSwap), a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $192K of DEX liquidity across 2 pools. Launch: launched on pump.fun (PumpSwap), under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`Hxceor...HCmM`](https://solscan.io/account/HxceordYrtSS9pEtE3TSifpgWH5AB4XRfCy2LpKHCmM) |
| **Network** | Solana |
| **Price** | $0.00001176 |
| **24h Volume** | $40.07M |
| **Liquidity** | $192.1K |
| **Volume / Liquidity** | 208.6× |
| **Token Age** | 11h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 35928 buys / 32756 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/gehmsyqlrlswxndnj5it3a93z3er7g4xga1x1njd3rsj)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/extended-sol-4e46)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-05*
