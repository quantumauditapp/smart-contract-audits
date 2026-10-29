---
token: Forever
ticker: FOREVER
network: solana
risk_score: 28
status: low
date: 2026-10-29
---

# Forever (FOREVER) — Smart Contract Security Analysis | Solana

> **Risk Score: 28/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/forever-sol)

---

## Audit Summary

The Forever (FOREVER) token mint has successfully revoked both mint and freeze authorities, mitigating central control risks. However, the protocol exhibits significant economic risks, including a 100% unlocked liquidity pool and a high volume-to-liquidity ratio indicative of wash trading. Holder concentration data was unavailable from the RPC source.

> **Final Recommendation:** Investors should exercise extreme caution due to the lack of locked liquidity, which allows the pool creator to withdraw all funds at any time. Monitor the liquidity pool for sudden withdrawals and avoid trading if the volume-to-liquidity ratio continues to deviate significantly from market norms.

Verify the current liquidity status via a block explorer before executing any trades. Given the absence of holder distribution data, avoid large positions that may be subject to liquidity exit risks.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the standard SPL Token program (7.1 Architecture). Both mint and freeze authorities are revoked (7.3 Access Control), ensuring the supply is fixed and accounts cannot be frozen. No… |
| **Governance / Economics** | 5/10 | Medium | The liquidity pool is entirely unlocked, with 0% burned or locked (7.4 Economic). The volume-to-liquidity ratio of 65.10 suggests artificial trading activity (7.6 External). Holder concentration data… |
| **Upgrades** | 8/10 | Low | The token metadata is immutable (7.7 Upgrades). There are no upgradeable components or transfer hooks (7.8 Operations). The mint state is final and cannot be modified by any authority. |

## Security Findings

_🟠 2 High · ⚪ 5 Informational_

### `H-01` — Pool Liquidity Not Locked  *(Severity: High · Status: Unresolved)*

0.0% of the pool's liquidity is burned or locked; the remaining liquidity can be withdrawn by the pool creator.

**Recommendation:** Lock or burn the majority of the liquidity pool to prevent rug-pull scenarios.


### `H-02` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume-to-liquidity ratio is 65.10, which is significantly higher than the 20x threshold, indicating potential wash trading.

**Recommendation:** Monitor trading activity for artificial volume patterns and exercise caution regarding price discovery.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity protection could not be verified  *(Severity: Informational · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 0.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. Solana LP holders are anonymous in the data we read, so who can withdraw the remaining liquidity cannot be verified.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $183K (DexScreener, all pools). 24h trading volume $11.5M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun (PumpSwap), a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $183K of DEX liquidity across 2 pools. Launch: launched on pump.fun (PumpSwap), under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`DdbvvL...YSd1`](https://solscan.io/account/DdbvvL4jJ8TKVk7BmCN6i741bwD5M44q1ofPse73YSd1) |
| **Network** | Solana |
| **Price** | $0.00000733 |
| **24h Volume** | $11.46M |
| **Liquidity** | $183.4K |
| **Volume / Liquidity** | 62.5× |
| **Token Age** | 5h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 17080 buys / 15548 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/95jlas4ymfzl9tlgnv6zzvqbkz7ispst97ut3pdfadhp)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/forever-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-29*
