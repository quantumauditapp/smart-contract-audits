---
token: Ilan Muhammad Ai Mask
ticker: IMAM
network: solana
risk_score: 12
status: low
date: 2026-11-07
---

# Ilan Muhammad Ai Mask (IMAM) — Smart Contract Security Analysis | Solana

> **Risk Score: 12/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/ilan-muhammad-ai-mask-sol)

---

## Audit Summary

The IMAM token utilizes the Token-2022 program with both mint and freeze authorities successfully revoked. While the protocol demonstrates strong security regarding authority control, it exhibits a high volume-to-liquidity ratio indicative of potential wash trading. Holder concentration data was unavailable, and 49.1% of liquidity remains unlocked.

> **Final Recommendation:** Investors should exercise caution regarding the high volume-to-liquidity ratio, which may not reflect organic demand. Monitor the liquidity pool for sudden withdrawals, as nearly half of the liquidity is not burned or locked.

Verify the current liquidity status via block explorers to ensure the pool remains stable before executing large trades. As holder concentration data is unavailable, avoid exposure to large positions that may be subject to high slippage or sudden sell-side pressure.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is built on the Token-2022 program, ensuring modern extension compatibility. 7.1 Architecture and 7.3 Access Control are robust as both mint and freeze authorities are revoked. 7.2 Code… |
| **Governance / Economics** | 7/10 | Low | 7.4 Economic stability is challenged by a volume-to-liquidity ratio of 25.24, suggesting artificial trading activity. 7.6 External market data shows $109,162 in liquidity, of which 50.9% is burned.… |
| **Upgrades** | 8/10 | Low | 7.7 Upgrades are not applicable as the mint is immutable. Metadata is fixed and non-mutable, preventing branding changes. No administrative authorities exist to modify token behavior or extensions. |

## Security Findings

_🟠 1 High · 🟡 2 Medium · ⚪ 4 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume-to-liquidity ratio is 25.24, which exceeds the 20x threshold, indicating potential artificial trade volume.

**Recommendation:** Monitor trading activity for organic patterns and exercise caution due to potential price manipulation.


### `M-01` — Pool Liquidity Not Locked  *(Severity: Medium · Status: Unresolved)*

Only 50.9% of liquidity is burned; the remaining 49.1% is not locked and could be withdrawn by the pool creator or current LP token holders.

**Recommendation:** Verify the liquidity provider's wallet activity and consider the risk of liquidity removal.


### `QA-LIQUIDITY` — Liquidity only partly locked or burned  *(Severity: Medium · Status: Acknowledged)*

50.9% of the pool's LP is burned or time-locked. 50.9% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. Solana LP holders are anonymous in the data we read, so who can withdraw the remaining liquidity cannot be verified.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $123K (DexScreener, all pools). 24h trading volume $1.6M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $123K of DEX liquidity across 9 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`75VDY6...pump`](https://solscan.io/account/75VDY6P9kJyAp7QGYRzq7o85oKBSXpR9XmaWVHcspump) |
| **Network** | Solana |
| **Price** | $0.0005382 |
| **24h Volume** | $1.59M |
| **Liquidity** | $117.0K |
| **Volume / Liquidity** | 13.6× |
| **Token Age** | 0h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 7067 buys / 5744 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/c7rynwvkjasvh8nt4q2pkecmhuerm1nrxobtsicueg3u)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/ilan-muhammad-ai-mask-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-07*
