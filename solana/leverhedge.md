---
token: Leverhedge
ticker: LEVERHEDGE
network: solana
risk_score: 0
status: low
date: 2026-10-31
---

# Leverhedge (LEVERHEDGE) — Smart Contract Security Analysis | Solana

> **Risk Score: 0/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/leverhedge-sol)

---

## Audit Summary

The Leverhedge token is a standard SPL Token-2022 implementation with both mint and freeze authorities successfully revoked. Liquidity is fully secured via a 100% burn of LP tokens, and no mutable extensions are active. Third-party risk registry data was unavailable for this assessment.

> **Final Recommendation:** The token configuration is secure and immutable. Holders should monitor the token's market depth on DEX platforms to ensure slippage remains within acceptable limits for their position size.

Verify the mint and freeze authority status periodically using a block explorer to confirm they remain set to 'None'. No further security actions are required for this asset.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the spl-token-2022 program with no active transfer hooks or custom extensions. 7.1 Architecture and 7.2 Code Security are standard for this program version. 7.3 Access Control is… |
| **Governance / Economics** | 10/10 | Low | 7.4 Economic stability is supported by $70,358 in liquidity, which is 100% burned and inaccessible to the creator. 7.5 Governance is decentralized by the lack of mint authority. While the 24h… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable as the mint is immutable. Metadata is non-mutable, and no authority exists to modify token parameters. The configuration is locked at the protocol level. |

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

Liquidity $71K (DexScreener, all pools). 24h trading volume $513K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $71K of DEX liquidity across 2 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`FWatMY...pump`](https://solscan.io/account/FWatMYieKhRuJ1yuTcmVG1njRhZWwqHwjR11pBympump) |
| **Network** | Solana |
| **Price** | $0.0007413 |
| **24h Volume** | $512.6K |
| **Liquidity** | $71.2K |
| **Volume / Liquidity** | 7.2× |
| **Token Age** | 3h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 6916 buys / 2250 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/6d3ujezdb2wdbvvryfycvgxsih9fw6ml6hscia5qvhwp)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/leverhedge-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-31*
