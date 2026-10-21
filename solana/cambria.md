---
token: Cambria
ticker: RSGP
network: solana
risk_score: 26
status: low
date: 2026-10-21
---

# Cambria (RSGP) — Smart Contract Security Analysis | Solana

> **Risk Score: 26/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/cambria-sol)

---

## Audit Summary

The Cambria (RSGP) token utilizes the standard SPL Token program with both mint and freeze authorities successfully revoked. However, the protocol exhibits high-risk economic indicators, specifically a volume-to-liquidity ratio suggesting potential wash trading and a complete lack of locked liquidity. Third-party registry data indicates that the liquidity pool is entirely unlocked, posing a significant risk of sudden withdrawal.

> **Final Recommendation:** Investors should exercise extreme caution due to the lack of locked liquidity, which allows for the potential removal of the entire pool by the creator. Monitor the liquidity pool for sudden withdrawals and verify the volume-to-liquidity ratio before executing large trades.

Verify the current liquidity status on-chain to ensure the pool remains active. Avoid interacting with the token if the liquidity pool is drained, as there is no mechanism to recover funds or force liquidity provision.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is initialized on the standard SPL Token program (7.1 Architecture). Both mint and freeze authorities are revoked, ensuring the supply is fixed and accounts cannot be frozen (7.3 Access… |
| **Governance / Economics** | 5/10 | Medium | The token exhibits a volume-to-liquidity ratio of 114.31, which is significantly above the 20x threshold, indicating potential wash trading (7.4 Economic). 100% of the pool liquidity is unlocked, and… |
| **Upgrades** | 8/10 | Low | The token mint is immutable with metadata_mutable set to False (7.7 Upgrades). There are no upgradeable components or proxy patterns in the SPL Token standard. Authority revocation is permanent and… |

## Security Findings

_🟠 2 High · 🟡 1 Medium · ⚪ 5 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume-to-liquidity ratio is 114.31, which exceeds the 20x threshold, indicating potential artificial trade volume.

**Recommendation:** Exercise caution; high volume relative to liquidity is often used to create a false sense of market demand.


### `H-02` — Pool Liquidity Not Locked  *(Severity: High · Status: Unresolved)*

0% of the pool liquidity is burned or locked, meaning the liquidity provider can withdraw all funds at any time.

**Recommendation:** Treat the pool as removable; do not assume liquidity will remain available for exit.


### `M-01` — Large Amount of LP Unlocked  *(Severity: Medium · Status: Unresolved)*

Third-party risk registry flags the token for having a large amount of unlocked liquidity, increasing the risk of a rug-pull scenario.

**Recommendation:** Monitor the liquidity provider's wallet activity for signs of imminent withdrawal.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity protection could not be verified  *(Severity: Informational · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 0.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. Solana LP holders are anonymous in the data we read, so who can withdraw the remaining liquidity cannot be verified.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $319K (DexScreener, all pools). 24h trading volume $34.9M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun (PumpSwap), a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $319K of DEX liquidity across 2 pools. Launch: launched on pump.fun (PumpSwap), under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`2qzVdw...hXrU`](https://solscan.io/account/2qzVdwoPsxW9RZKkgEBU5Vr3xz8hqRJXfCyeSPVvhXrU) |
| **Network** | Solana |
| **Price** | $0.00001602 |
| **24h Volume** | $34.86M |
| **Liquidity** | $318.6K |
| **Volume / Liquidity** | 109.4× |
| **Token Age** | 5h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 16998 buys / 15342 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/gupgi7i5wkhgcwlhxpghlspzsldht7yhtb5sadm29lhy)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/cambria-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-21*
