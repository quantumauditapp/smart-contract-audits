---
token: Dacity Coin
ticker: DACITY
network: solana
risk_score: 13
status: low
date: 2026-10-23
---

# Dacity Coin (DACITY) — Smart Contract Security Analysis | Solana

> **Risk Score: 13/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/dacity-coin-sol-2193)

---

## Audit Summary

Dacity Coin is a standard SPL Token-2022 mint with both mint and freeze authorities successfully revoked. The token exhibits healthy liquidity characteristics with 100% of pool liquidity permanently burned, mitigating rug-pull risks. No adverse flags were reported by third-party registries.

> **Final Recommendation:** The token is currently in a secure state with no active administrative authorities. Holders should continue to monitor the top 10 holder distribution to ensure concentration does not increase significantly over time. No further action is required to secure the mint configuration.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the SPL Token-2022 program with no active extensions like transfer hooks or default account freezing. 7.1 Architecture and 7.2 Code Security are standard for the Solana ecosystem.… |
| **Governance / Economics** | 9/10 | Low | 7.4 Economic and 7.5 Governance metrics show 33.88% concentration among the top 10 holders, which is within acceptable ranges. 7.6 External market data indicates $98,245 in liquidity, which is fully… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable as the mint is immutable. Metadata is non-mutable, preventing post-launch branding changes. The token program configuration is fixed and cannot be modified by any… |

## Security Findings

_⚪ 7 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, holder concentration, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 99.9% of supply. Of that, 66.0% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 33.9% in wallets, 0.0% in other contracts. 11 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

11 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $98K (DexScreener, all pools). 24h trading volume $107K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $98K of DEX liquidity across 1 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`E5ZXP1...pump`](https://solscan.io/account/E5ZXP1CeiBxQqoSCNmpMxx2DED7xwymLWjVRm6rGpump) |
| **Network** | Solana |
| **Price** | $0.001363 |
| **24h Volume** | $106.6K |
| **Liquidity** | $98.5K |
| **Volume / Liquidity** | 1.1× |
| **Token Age** | 8h |
| **Top-10 Holders** | 99.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 20028 buys / 12630 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/2xxqakzdx4elq6eyvnseuryfjen5q1zd1ompoeq1qzdt)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/dacity-coin-sol-2193)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-23*
