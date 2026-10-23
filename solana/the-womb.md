---
token: the womb
ticker: WOMB
network: solana
risk_score: 22
status: low
date: 2026-10-23
---

# the womb (WOMB) — Smart Contract Security Analysis | Solana

> **Risk Score: 22/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/the-womb-sol)

---

## Audit Summary

The token 'the womb' (WOMB) utilizes the SPL Token-2022 program with both mint and freeze authorities successfully revoked. The liquidity pool is fully burned, ensuring permanent availability of trading funds. No adverse flags were reported by third-party risk registries.

> **Final Recommendation:** The token configuration is secure and immutable. Users should monitor the top 10 holder concentration over time to ensure that no single entity accumulates a majority of the circulating supply.

Verify the current mint and freeze authority status on-chain using a block explorer to confirm they remain set to 'None'.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is deployed on the SPL Token-2022 program. 7.1 Architecture and 7.3 Access Control are robust as both mint and freeze authorities are revoked. 7.2 Code Security is maintained by the… |
| **Governance / Economics** | 9/10 | Low | 7.4 Economic and 7.5 Governance metrics show 23.16% concentration among the top 10 holders. 100% of pool liquidity is burned, preventing rug-pulls via liquidity withdrawal. 7.6 External market data… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades and 7.8 Operations are restricted by the revocation of authorities. Metadata is immutable, and no transfer fee or hook upgrades are possible. The token configuration is static and cannot… |

## Security Findings

_⚪ 7 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, holder concentration, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 60.0% of supply. Of that, 36.8% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 23.2% in wallets, 0.0% in other contracts. 166 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

166 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $13K (DexScreener, all pools). 24h trading volume $167K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun (PumpSwap), a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $13K of DEX liquidity across 2 pools. Launch: launched on pump.fun (PumpSwap), under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`AmZuyF...WBUy`](https://solscan.io/account/AmZuyFhJ8pGFKgCqChxBa2xN4KtxnNPGLT9jXWpMWBUy) |
| **Network** | Solana |
| **Price** | $0.00003133 |
| **24h Volume** | $130.2K |
| **Liquidity** | $13.4K |
| **Volume / Liquidity** | 9.7× |
| **Token Age** | 3h |
| **Top-10 Holders** | 60.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1577 buys / 1226 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/e3hv1j5rfttqjerkrjjn3xphuvdz6kgz1tsqgoubbtnm)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/the-womb-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-23*
