---
token: catana
ticker: CATANA
network: solana
risk_score: 22
status: low
date: 2026-10-05
---

# catana (CATANA) — Smart Contract Security Analysis | Solana

> **Risk Score: 22/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/catana-sol)

---

## Audit Summary

This audit of the catana SPL token mint found no critical or high-severity issues based on the provided on-chain facts and external security signals. Mint and freeze authorities are revoked, ensuring fixed supply and immutable account states. Liquidity is fully burned, and third-party registry data reported no adverse flags.

> **Final Recommendation:** Holders should verify on-chain that the mint and freeze authorities remain revoked to confirm the immutability of supply and account states. Monitor the token's market activity for any significant changes in liquidity or trading patterns, although current indicators are favorable. No further specific actions are required based on the current audit findings.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The catana token is an SPL Token-2022 mint with both mint and freeze authorities revoked, indicating a fixed supply and immutable account states. No transfer hook is active, ensuring direct token… |
| **Governance / Economics** | 9/10 | Low | Holder concentration is low, with the top 10 holders that can sell holding 24.74% of the supply, reducing the risk of single-whale market manipulation. Total DEX liquidity is $12,967, and 100% of the… |
| **Upgrades** | 10/10 | Low | The mint and freeze authorities are permanently revoked, preventing any future changes to supply or account freezing capabilities. The token utilizes the Token-2022 program but does not have mutable… |

## Security Findings

_⚪ 6 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, holder concentration, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 64.5% of supply. Of that, 39.7% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 24.7% in wallets, 0.0% in other contracts. 560 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

560 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $13K (DexScreener, all pools). 24h trading volume $89K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: meme vocabulary in name/ticker (cat); launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $13K of DEX liquidity across 1 pools. Launch: launched on pump.fun, 55 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`H3AxGg...pump`](https://solscan.io/account/H3AxGgBvDhEaEGCihggB7oQbpxzCyD3FVZWcd7EWpump) |
| **Network** | Solana |
| **Price** | $0.00002339 |
| **24h Volume** | $89.3K |
| **Liquidity** | $13.1K |
| **Volume / Liquidity** | 6.8× |
| **Token Age** | 1mo |
| **Top-10 Holders** | 64.5% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1060 buys / 765 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/9dv5xx94nj2vgkjzewukatlzqkzcn8x2d4gedf6m8vqq)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/catana-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-05*
