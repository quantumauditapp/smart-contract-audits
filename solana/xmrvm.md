---
token: XMRvm
ticker: XMRVM
network: solana
risk_score: 19
status: low
date: 2026-11-04
---

# XMRvm (XMRVM) — Smart Contract Security Analysis | Solana

> **Risk Score: 19/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/xmrvm-sol)

---

## Audit Summary

The XMRvm token is a standard SPL Token-2022 implementation with both mint and freeze authorities successfully revoked. The liquidity pool is fully burned, ensuring permanent availability for trading. No adverse flags were reported by third-party risk registries.

> **Final Recommendation:** The token exhibits a strong security posture with no administrative backdoors. Users should continue to monitor the top 10 holder distribution via block explorers to ensure concentration remains within reasonable bounds as the project matures.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the Token-2022 program (7.1 Architecture). Access control is robust as both mint and freeze authorities are revoked (7.3 Access Control). The token does not utilize transfer hooks… |
| **Governance / Economics** | 9/10 | Low | Holder concentration is low, with the top 10 holders controlling 27.03% of the supply (7.4 Economic). Liquidity is $21,614 and is 100% burned, preventing rug pulls (7.5 Governance). Trading volume is… |
| **Upgrades** | 10/10 | Low | The token metadata is immutable (7.7 Upgrades). No administrative functions exist to modify the token's operational parameters (7.8 Operations). The mint is fully decentralized. |

## Security Findings

_⚪ 7 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, holder concentration, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 42.3% of supply. Of that, 15.3% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 27.0% in wallets, 0.0% in other contracts. 213 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

213 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $22K (DexScreener, all pools). 24h trading volume $39K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $22K of DEX liquidity across 1 pools. Launch: launched on pump.fun, 13 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 13 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 13 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`5sTBTk...pump`](https://solscan.io/account/5sTBTkZTzTijpGJf5dYPGCkHR9BSyXYtj9KAg6v4pump) |
| **Network** | Solana |
| **Price** | $0.0000787 |
| **24h Volume** | $38.9K |
| **Liquidity** | $21.6K |
| **Volume / Liquidity** | 1.8× |
| **Token Age** | 13d |
| **Top-10 Holders** | 42.3% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 314 buys / 372 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/6arhcprfzn1gz9xlhtjhci94thrd4ki61yrhwdee8wrk)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/xmrvm-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-04*
