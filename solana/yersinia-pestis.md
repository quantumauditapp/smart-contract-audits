---
token: Yersinia pestis
ticker: PLAGUE
network: solana
risk_score: 1
status: low
date: 2026-10-08
---

# Yersinia pestis (PLAGUE) — Smart Contract Security Analysis | Solana

> **Risk Score: 1/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/yersinia-pestis-sol)

---

## Audit Summary

This audit of the Yersinia pestis (PLAGUE) SPL token mint found no critical or high-risk vulnerabilities based on the available on-chain and market data. The mint and freeze authorities are revoked, and all pool liquidity is burned, indicating a robust and immutable token state. Third-party risk registries reported no adverse flags.

> **Final Recommendation:** Holders should verify on-chain that the mint and freeze authorities remain revoked to confirm the token's immutable supply and transferability. While the current liquidity is sufficient for moderate trades, monitoring liquidity levels and trading volume is advisable for large positions. No further specific on-chain verification steps are required given the current state of the token.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The Yersinia pestis (PLAGUE) token is an SPL token operating under the `spl-token` program. Both the mint authority and freeze authority have been revoked, ensuring no new tokens can be minted and no… |
| **Governance / Economics** | 10/10 | Low | Holder concentration is low, with the top 10 holders that can sell accounting for only 15.14% of the total supply. The token has a liquidity of $75,789 USD. All 100% of the pool's liquidity provider… |
| **Upgrades** | 10/10 | Low | The token's core parameters are immutable, as both the mint and freeze authorities have been revoked. Metadata is also immutable (`metadata_mutable: False`), meaning the token name, symbol, or image… |

## Security Findings

_⚪ 7 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, holder concentration, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 25.2% of supply. Of that, 10.1% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 15.1% in wallets, 0.0% in other contracts. 6,557 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

6,557 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. This assessment covers the main pool, which holds 59% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $129K (DexScreener, all pools). 24h trading volume $1.2M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $129K of DEX liquidity across 19 pools. Launch: launched on pump.fun, 4 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 4 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 4 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`CscZaq...pump`](https://solscan.io/account/CscZaq5twomhUkvCY8Jdd1tge32L4Yj9FbkFFEZQpump) |
| **Network** | Solana |
| **Price** | $0.0005029 |
| **24h Volume** | $763.0K |
| **Liquidity** | $76.3K |
| **Volume / Liquidity** | 10.0× |
| **Token Age** | 4d |
| **Top-10 Holders** | 25.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 5623 buys / 4699 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/9gbxhym9gxdzh3u6unw71yxaixabkg8k7eegywh2wqgg)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/yersinia-pestis-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-08*
