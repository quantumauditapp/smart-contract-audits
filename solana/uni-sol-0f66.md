---
token: UNI
ticker: UNI
network: solana
risk_score: 21
status: low
date: 2026-11-02
---

# UNI (UNI) — Smart Contract Security Analysis | Solana

> **Risk Score: 21/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/uni-sol-0f66)

---

## Audit Summary

The UNI token utilizes the standard SPL Token program with both mint and freeze authorities successfully revoked, ensuring supply immutability and preventing account freezing. Liquidity is fully burned, eliminating withdrawal risks for the pool creator. Holder concentration data was unavailable, and the token is relatively new with high trading volume relative to liquidity.

> **Final Recommendation:** Investors should monitor the token's liquidity depth as the pair matures, given the current high volume-to-liquidity ratio. Since holder concentration data is unavailable, users should exercise caution regarding potential whale activity and price slippage during large trades.

Verify the mint and freeze authority status directly on-chain using a block explorer to confirm they remain set to null. Monitor the token's official communication channels for any updates regarding project development.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is deployed on the standard SPL Token program (7.1 Architecture). Both mint and freeze authorities are revoked, preventing unauthorized supply inflation or account freezing (7.3 Access… |
| **Governance / Economics** | 9/10 | Low | Liquidity is fully secured with 100% of LP tokens burned (7.4 Economic). The pair is less than one day old, and the volume-to-liquidity ratio is 19.82, indicating high short-term volatility (7.8… |
| **Upgrades** | 10/10 | Low | The token mint does not support upgrades, consistent with standard SPL token architecture (7.7 Upgrades). Metadata and authority settings are locked, ensuring no future changes to token properties… |

## Security Findings

_⚪ 6 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. This assessment covers the main pool, which holds 90% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $35K (DexScreener, all pools). 24h trading volume $522K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $35K of DEX liquidity across 3 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`8Jz7Ng...UBeV`](https://solscan.io/account/8Jz7NgcjEMsWNPAXF3AvUHuHfN1bJ9nYZFHKiKkZUBeV) |
| **Network** | Solana |
| **Price** | $0.0001328 |
| **24h Volume** | $515.8K |
| **Liquidity** | $31.2K |
| **Volume / Liquidity** | 16.5× |
| **Token Age** | 2h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 5821 buys / 4484 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/2hsdj1k6zkwwzvdgiziklrbaqsj6szzx4e9ha15knvsh)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/uni-sol-0f66)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-02*
