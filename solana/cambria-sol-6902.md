---
token: Cambria
ticker: RSGP
network: solana
risk_score: 29
status: low
date: 2026-10-29
---

# Cambria (RSGP) — Smart Contract Security Analysis | Solana

> **Risk Score: 29/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/cambria-sol-6902)

---

## Audit Summary

The Cambria (RSGP) token utilizes the standard SPL Token program with both mint and freeze authorities successfully revoked. However, the protocol exhibits significant economic risks, specifically a high volume-to-liquidity ratio suggesting potential wash trading and 100% of pool liquidity remaining unlocked. Holder concentration data was unavailable from the provided sources.

> **Final Recommendation:** Investors should exercise extreme caution regarding the liquidity pool, as the lack of locked liquidity allows for potential removal by the pool creator. Monitor the pool's liquidity depth and the volume-to-liquidity ratio to identify potential exit liquidity risks before executing trades.

Verify current holder distribution using block explorers to assess if supply is concentrated among a few wallets. Given the high volume-to-liquidity ratio, avoid relying on 24-hour volume as a signal of organic market demand.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token operates on the standard SPL Token program (7.1 Architecture). Access control is robust as both mint and freeze authorities are revoked (7.3 Access Control). The token does not utilize… |
| **Governance / Economics** | 5/10 | Medium | Economic stability is compromised by a volume-to-liquidity ratio of 56.05, indicating potential artificial trading activity (7.4 Economic). 100% of the pool liquidity is unlocked, posing a risk of… |
| **Upgrades** | 8/10 | Low | The token metadata is immutable, preventing post-launch branding changes (7.7 Upgrades). There are no upgradeable components or proxy patterns inherent to this SPL token (7.7 Upgrades). The mint and… |

## Security Findings

_🟠 2 High · 🟡 1 Medium · ⚪ 5 Informational_

### `H-01` — Pool Liquidity Not Locked  *(Severity: High · Status: Unresolved)*

100% of the pool's liquidity is unlocked and can be withdrawn by the pool creator, as 0.0% of LP tokens are burned or locked.

**Recommendation:** The project team should lock or burn the majority of LP tokens to ensure market stability and prevent rug-pull scenarios.


### `H-02` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume-to-liquidity ratio is 56.05, which significantly exceeds the 20x threshold, indicating likely artificial trade volume.

**Recommendation:** Exercise caution; high volume relative to liquidity is often used to create a false impression of market interest.


### `M-01` — Large Amount of LP Unlocked  *(Severity: Medium · Status: Unresolved)*

Third-party risk registry flags indicate that a large amount of liquidity is currently unlocked, increasing the risk of sudden liquidity removal.

**Recommendation:** Monitor the liquidity provider wallet addresses for any significant movements or withdrawals.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity protection could not be verified  *(Severity: Informational · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 0.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. Solana LP holders are anonymous in the data we read, so who can withdraw the remaining liquidity cannot be verified.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $174K (DexScreener, all pools). 24h trading volume $9.5M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun (PumpSwap), a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $174K of DEX liquidity across 2 pools. Launch: launched on pump.fun (PumpSwap), under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`7SiWjb...uUAq`](https://solscan.io/account/7SiWjbbM3HBmDEyWz4z5RHFW8QQx6u3b3cXMBVfYuUAq) |
| **Network** | Solana |
| **Price** | $0.00000729 |
| **24h Volume** | $9.49M |
| **Liquidity** | $174.0K |
| **Volume / Liquidity** | 54.5× |
| **Token Age** | 6h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 18534 buys / 16798 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/71jjypykfzfvly8keuinruiys5ubodtwmv9gnyismze6)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/cambria-sol-6902)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-29*
