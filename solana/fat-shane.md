---
token: Fat Shane
ticker: SHANE
network: solana
risk_score: 40
status: medium
date: 2026-11-07
---

# Fat Shane (SHANE) — Smart Contract Security Analysis | Solana

> **Risk Score: 40/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/fat-shane-sol)

---

## Audit Summary

The Fat Shane (SHANE) token is a Token-2022 asset with both mint and freeze authorities successfully revoked. The primary risks identified are very low liquidity and a high volume-to-liquidity ratio, which suggests potential wash trading. Holder distribution data was unavailable for this analysis.

> **Final Recommendation:** Investors should exercise extreme caution due to the low liquidity, which may prevent the execution of large sell orders without significant price impact. Monitor the token's trading volume relative to liquidity to avoid assets exhibiting artificial volume patterns.

Verify the current supply and holder distribution using a block explorer to ensure the token's distribution aligns with your risk tolerance. Do not rely on high volume metrics as a signal of organic demand.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The token utilizes the Token-2022 program with no active transfer hooks or default frozen states. 7.1 Architecture is standard for SPL tokens, and 7.3 Access Control is robust as both mint and freeze… |
| **Governance / Economics** | 5/10 | Medium | 7.4 Economic factors are concerning due to the very low liquidity of $6,495. 7.6 External signals indicate a high volume-to-liquidity ratio of 33.28, which is a common indicator of wash trading. 7.5… |
| **Upgrades** | 8/10 | Low | 7.7 Upgrades are not applicable as the mint is immutable. Metadata is non-mutable, and no authority exists to modify token parameters. The token state is fixed and cannot be altered by any external… |

## Security Findings

_🟠 2 High · 🟡 1 Medium · ⚪ 4 Informational_

### `H-01` — Very Low Liquidity  *(Severity: High · Status: Unresolved)*

Total DEX liquidity is $6,495. Slippage will be severe; large positions cannot be exited without significant loss.

**Recommendation:** Ensure position sizes are small relative to the total liquidity pool.


### `H-02` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

24-hour volume is 33.28x liquidity — a pattern strongly associated with artificially inflated trade volume.

**Recommendation:** Perform independent verification of trade history before assuming organic market interest.


### `QA-MARKET` — The market for this token  *(Severity: Medium · Status: Acknowledged)*

Liquidity $9K (DexScreener, all pools). 24h trading volume $269K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $9K of DEX liquidity across 9 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`5CVJ8W...pump`](https://solscan.io/account/5CVJ8W52Z41KRfAYHnpJTSMx4eP5ZThGDZ5tW7R8pump) |
| **Network** | Solana |
| **Price** | $0.00001843 |
| **24h Volume** | $209.8K |
| **Liquidity** | $9.4K |
| **Volume / Liquidity** | 22.4× |
| **Token Age** | 1h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 3946 buys / 2945 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/aczdfzeefek1gafhejhno8kxivfupmdrmtj81v3aiebs)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/fat-shane-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-07*
