---
token: Extended
ticker: XTEN
network: solana
risk_score: 27
status: low
date: 2026-11-04
---

# Extended (XTEN) — Smart Contract Security Analysis | Solana

> **Risk Score: 27/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/extended-sol-7d59)

---

## Audit Summary

The Extended (XTEN) token utilizes the standard SPL Token program with both mint and freeze authorities successfully revoked. However, the protocol exhibits significant economic risks, including a high volume-to-liquidity ratio indicative of wash trading and a complete lack of locked liquidity. Holder concentration data was unavailable from the provided sources.

> **Final Recommendation:** Investors should exercise extreme caution due to the lack of locked liquidity and the high probability of artificial trading volume. Monitor the liquidity pool for sudden withdrawals, as the current lack of locking mechanisms allows for potential removal of all pool funds.

Verify the current liquidity status via block explorers to ensure the pool creator has not removed funds. Avoid trading during periods of extreme volatility, as the high volume-to-liquidity ratio suggests that market depth may be significantly lower than reported.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is initialized on the standard spl-token program (7.1 Architecture). Both mint and freeze authorities are revoked, ensuring no further supply inflation or account freezing (7.3 Access… |
| **Governance / Economics** | 5/10 | Medium | Liquidity is $177,734 with 0% burned or locked, posing a risk of withdrawal (7.4 Economic). The 24h volume of $45,032,101 results in a ratio of 253.37, which is a strong signal of wash trading (7.8… |
| **Upgrades** | 8/10 | Low | The token metadata is immutable, preventing post-launch branding changes (7.7 Upgrades). There are no upgradeable components or proxies associated with this SPL mint (7.2 Code Security). |

## Security Findings

_🟠 2 High · 🟡 1 Medium · ⚪ 5 Informational_

### `H-01` — Very Low Liquidity / High Risk of Withdrawal  *(Severity: High · Status: Unresolved)*

0.0% of the pool's liquidity is burned or locked, and the identity of the liquidity providers is anonymous, meaning the pool creator or current holders can withdraw all liquidity at any time.

**Recommendation:** Lock or burn the liquidity pool tokens to protect users from a sudden liquidity removal event.


### `H-02` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The volume/liquidity ratio is 253.37, which significantly exceeds the threshold of 20, indicating that the reported trading volume is likely artificially inflated.

**Recommendation:** Do not rely on volume metrics as an indicator of genuine market interest or liquidity depth.


### `M-01` — Large Amount of LP Unlocked  *(Severity: Medium · Status: Unresolved)*

Third-party risk registry signals indicate a large amount of liquidity is currently unlocked, increasing the risk of a rug-pull scenario.

**Recommendation:** Verify the liquidity provider's wallet activity and ensure that the protocol has established a formal liquidity locking mechanism.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity protection could not be verified  *(Severity: Informational · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 0.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. Solana LP holders are anonymous in the data we read, so who can withdraw the remaining liquidity cannot be verified.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $168K (DexScreener, all pools). 24h trading volume $43.4M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun (PumpSwap), a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $168K of DEX liquidity across 2 pools. Launch: launched on pump.fun (PumpSwap), under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`E8kM1h...H3tg`](https://solscan.io/account/E8kM1hqxLwUUtZwGBrGkoQcdLA6aDjmL9rx58ectH3tg) |
| **Network** | Solana |
| **Price** | $0.00001243 |
| **24h Volume** | $43.42M |
| **Liquidity** | $167.7K |
| **Volume / Liquidity** | 258.8× |
| **Token Age** | 12h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 38707 buys / 35354 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/4sq1m4mb6mybz4qk1vn6tszjsypylvjwtepe787xhceu)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/extended-sol-7d59)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-04*
