---
token: Soul Labs
ticker: SO
network: solana
risk_score: 29
status: low
date: 2026-10-22
---

# Soul Labs (SO) — Smart Contract Security Analysis | Solana

> **Risk Score: 29/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/soul-labs-sol-9c1c)

---

## Audit Summary

The Soul Labs token mint exhibits high risk due to extreme wash-trading indicators and the lack of locked liquidity. While the mint and freeze authorities are correctly revoked, the liquidity pool is entirely unlocked, and third-party registry data flags the project as high-risk due to these liquidity movements. Holder concentration data was unavailable for this audit.

> **Final Recommendation:** Investors should exercise extreme caution due to the lack of locked liquidity and suspicious trading volume. Monitor the liquidity pool for sudden withdrawals, as the current structure allows for the total removal of backing assets by anonymous parties.

Verify the current liquidity status on-chain before interacting with the token. Avoid large positions given the high probability of artificial volume and the risk of liquidity removal.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the standard spl-token program (7.1 Architecture). Both mint and freeze authorities are revoked, preventing further supply inflation or account freezing (7.3 Access Control). The… |
| **Governance / Economics** | 5/10 | Medium | The token exhibits a volume/liquidity ratio of 262.41, which is a strong signal of wash trading (7.4 Economic). Liquidity is $365,223, but 100% of the pool remains unlocked and withdrawable by… |
| **Upgrades** | 8/10 | Low | The token metadata is immutable, and there are no upgradeable extensions enabled (7.7 Upgrades). The mint state is fixed, and no further modifications to the token program logic are possible (7.8… |

## Security Findings

_🟠 2 High · 🟡 1 Medium · ⚪ 5 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume/liquidity ratio is 262.41, significantly exceeding the 20x threshold, indicating artificially inflated trade volume.

**Recommendation:** Account for the high probability of manipulated volume when assessing market demand.


### `H-02` — Pool Liquidity Not Locked  *(Severity: High · Status: Unresolved)*

0% of the pool's liquidity is burned or locked, meaning the entire liquidity pool can be withdrawn by the anonymous holders of the LP tokens.

**Recommendation:** Monitor the pool for liquidity removal; treat the pool as temporary.


### `M-01` — Flagged High-Risk by Third-Party Registry  *(Severity: Medium · Status: Unresolved)*

An independent third-party risk registry has flagged this token as high-risk due to the large amount of unlocked liquidity.

**Recommendation:** Review the project's liquidity management strategy before proceeding.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity protection could not be verified  *(Severity: Informational · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 0.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. Solana LP holders are anonymous in the data we read, so who can withdraw the remaining liquidity cannot be verified.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $353K (DexScreener, all pools). 24h trading volume $91.2M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun (PumpSwap), a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $353K of DEX liquidity across 2 pools. Launch: launched on pump.fun (PumpSwap), under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`Ecmsss...mmCM`](https://solscan.io/account/Ecmsss7ijkFgaWoXR7YN4zmiYPZRBKwRwddFc4ymmmCM) |
| **Network** | Solana |
| **Price** | $0.00002676 |
| **24h Volume** | $91.22M |
| **Liquidity** | $353.2K |
| **Volume / Liquidity** | 258.3× |
| **Token Age** | 14h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 43170 buys / 39234 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/cqvhfnjpaffyd1b1rvrr3ackkvidd5gt3ehk8ai6dkex)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/soul-labs-sol-9c1c)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-22*
