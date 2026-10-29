---
token: Hexncoin
ticker: HEXN
network: solana
risk_score: 16
status: low
date: 2026-10-29
---

# Hexncoin (HEXN) — Smart Contract Security Analysis | Solana

> **Risk Score: 16/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/hexncoin-sol)

---

## Audit Summary

Hexncoin is a Token-2022 asset with fully revoked mint and freeze authorities, providing strong protection against unauthorized supply inflation or account freezing. However, the token exhibits a high volume-to-liquidity ratio, suggesting potential wash trading activity. Holder concentration data is currently unavailable, and the asset is newly launched.

> **Final Recommendation:** Investors should exercise caution regarding the high volume-to-liquidity ratio, which may indicate artificial trading activity rather than organic demand. Monitor the asset for sustained liquidity growth before committing significant capital.

Verify that no new minting or freezing events occur by checking the mint account state on a block explorer. Given the lack of holder distribution data, avoid large market orders that could be impacted by low liquidity or potential hidden whale positions.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the SPL Token-2022 program with all critical authorities revoked (7.3 Access Control). The mint and freeze authorities are set to None, ensuring supply immutability and preventing… |
| **Governance / Economics** | 8/10 | Low | Liquidity is $50,631, with 100% of LP tokens burned, preventing rug-pulls via liquidity withdrawal (7.4 Economic). The 24h volume of $2,454,154 results in a volume/liquidity ratio of 48.47, which… |
| **Upgrades** | 10/10 | Low | The token metadata is immutable, and no upgradeable extensions are present (7.7 Upgrades). There is no mechanism for the developer to modify token parameters post-deployment (7.6 External). |

## Security Findings

_🟠 1 High · ⚪ 5 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume/liquidity ratio is 48.47, which is significantly higher than the 20x threshold, indicating potential wash trading.

**Recommendation:** Monitor trading activity for organic volume and verify liquidity depth before executing large trades.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $76K (DexScreener, all pools). 24h trading volume $2.3M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $76K of DEX liquidity across 1 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`ANVLA6...pump`](https://solscan.io/account/ANVLA6eKiAq4nstD2Sg3SZhfVkSEwfnGccn12UQWpump) |
| **Network** | Solana |
| **Price** | $0.0007622 |
| **24h Volume** | $2.28M |
| **Liquidity** | $75.5K |
| **Volume / Liquidity** | 30.2× |
| **Token Age** | 4h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 32214 buys / 12043 sells |

## Security Flags (4/4 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/solana/bqjzersgugnhav8c1m3vc4wa6mgqbae8t2w7eptsdkw4)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/hexncoin-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-29*
