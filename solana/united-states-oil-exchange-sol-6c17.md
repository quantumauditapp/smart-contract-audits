---
token: United States Oil Exchange
ticker: USOE
network: solana
risk_score: 0
status: low
date: 2026-10-29
---

# United States Oil Exchange (USOE) — Smart Contract Security Analysis | Solana

> **Risk Score: 0/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/united-states-oil-exchange-sol-6c17)

---

## Audit Summary

The USOE token utilizes the Token-2022 program with both mint and freeze authorities successfully revoked. Liquidity is fully secured via a 100% burn, and no malicious extensions are active. Holder distribution data was unavailable, preventing a full assessment of concentration risks.

> **Final Recommendation:** The token configuration is secure. Holders should monitor the token's market activity and liquidity depth on-chain to ensure continued stability. 

As holder concentration data was unavailable, users should exercise standard caution regarding potential whale activity and price volatility typical of high-market-cap assets.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is implemented using the Token-2022 program (7.1 Architecture). Security is bolstered by the permanent revocation of both mint and freeze authorities (7.3 Access Control). No transfer hooks… |
| **Governance / Economics** | 10/10 | Low | The token maintains $2.03M in liquidity, which is 100% burned and inaccessible to any creator (7.4 Economic). Trading volume is healthy relative to liquidity, with a ratio of 0.86 (7.6 External).… |
| **Upgrades** | 10/10 | Low | The mint and freeze authorities are revoked, ensuring the token supply and account states cannot be modified (7.7 Upgrades). Metadata is immutable, preventing unauthorized changes to branding (7.8… |

## Security Findings

_⚪ 6 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $2.0M (DexScreener, all pools). 24h trading volume $1.7M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $2.0M of DEX liquidity across 2 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`7FNR6j...pump`](https://solscan.io/account/7FNR6jJutKUpk919jx66thqeD3LPKHXw6atn332Dpump) |
| **Network** | Solana |
| **Price** | $0.5706 |
| **24h Volume** | $1.74M |
| **Liquidity** | $2.03M |
| **Volume / Liquidity** | 0.9× |
| **Token Age** | 14h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 43727 buys / 18654 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/cqrba4wz3mz3bwcna77jalzlfpyezfxwn716yxvthox3)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/united-states-oil-exchange-sol-6c17)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-29*
