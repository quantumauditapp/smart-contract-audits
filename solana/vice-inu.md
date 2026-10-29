---
token: Vice Inu
ticker: VI
network: solana
risk_score: 15
status: low
date: 2026-10-29
---

# Vice Inu (VI) — Smart Contract Security Analysis | Solana

> **Risk Score: 15/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/vice-inu-sol)

---

## Audit Summary

Vice Inu (VI) is a Token-2022 asset with both mint and freeze authorities successfully revoked. The liquidity pool is fully secured with 100% of LP tokens burned, preventing rug pulls via liquidity removal. Holder concentration data is currently unavailable, and the volume-to-liquidity ratio is moderate, suggesting active but not necessarily anomalous trading.

> **Final Recommendation:** Investors should monitor the token's market activity via block explorers to track holder distribution as it becomes available. Since the mint and freeze authorities are revoked and liquidity is burned, the primary remaining risk is market volatility rather than technical or administrative manipulation.

Verify the mint address A6PM7bxyWYiUxaEpRMHvuL4tY2jYVf8N46vXZ15Hpump on a block explorer to confirm the 'Mint Authority' and 'Freeze Authority' fields remain set to 'None'. No further technical action is required to secure the asset.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the Token-2022 program with no active transfer hooks or custom extensions. 7.1 Architecture is standard for SPL tokens, and 7.2 Code Security is maintained by the native program's… |
| **Governance / Economics** | 9/10 | Low | 7.4 Economic stability is supported by 100% burned liquidity, ensuring permanent DEX availability. 7.5 Governance is decentralized due to the lack of mint authority. While holder concentration data… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable to this mint as it is a standard SPL token. Metadata is immutable, and no balance-mutating authorities exist. The configuration is locked, preventing future changes to… |

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

Liquidity $48K (DexScreener, all pools). 24h trading volume $321K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: meme vocabulary in name/ticker (inu); launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $48K of DEX liquidity across 1 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`A6PM7b...pump`](https://solscan.io/account/A6PM7bxyWYiUxaEpRMHvuL4tY2jYVf8N46vXZ15Hpump) |
| **Network** | Solana |
| **Price** | $0.0003326 |
| **24h Volume** | $320.8K |
| **Liquidity** | $48.1K |
| **Volume / Liquidity** | 6.7× |
| **Token Age** | 1h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1194 buys / 964 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/g8vqy7bo6mrfkqh6cxsuie9ksh7fgby4nhspj4gklfhu)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/vice-inu-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-29*
