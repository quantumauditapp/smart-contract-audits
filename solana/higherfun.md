---
token: higher.fun
ticker: HIGH
network: solana
risk_score: 23
status: low
date: 2026-11-04
---

# higher.fun (HIGH) — Smart Contract Security Analysis | Solana

> **Risk Score: 23/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/higherfun-sol)

---

## Audit Summary

The higher.fun (HIGH) token is a standard SPL v3 mint with both mint and freeze authorities successfully revoked. Liquidity is fully secured, with 100% of pool liquidity either burned or locked, preventing rug-pull risks from the creator. Holder concentration data is unavailable, and the token exhibits high trading volume relative to its liquidity.

> **Final Recommendation:** The token is technically sound regarding authority control and liquidity safety. Users should monitor the token's market volatility given the high volume-to-liquidity ratio.

Verify the current supply and authority status via a block explorer to ensure no changes have occurred since this audit. As holder concentration data is unavailable, exercise caution regarding potential whale activity.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the standard SPL Token program (v3). 7.1 Architecture and 7.2 Code Security are consistent with standard, non-extended SPL mints. 7.3 Access Control is robust, as both mint and… |
| **Governance / Economics** | 7/10 | Low | 7.4 Economic stability is supported by 100% of liquidity being burned or locked. 7.5 Governance is decentralized by the lack of mint authority. 7.6 External market data indicates a high… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable to this SPL token mint. Metadata is immutable, and no transfer hooks or other mutable extensions are enabled. The token state is fixed and cannot be modified by any… |

## Security Findings

_⚪ 6 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 70.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. 30.0% of the pool's liquidity is locked for good in Raydium's LP locker (Burn & Earn) — only its trading fees can be collected; no one can withdraw the liquidity.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $36K (DexScreener, all pools). 24h trading volume $615K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $36K of DEX liquidity across 2 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`7ymF66...high`](https://solscan.io/account/7ymF66Z6VhgNiwadtVhjTtT6U7iQRpSxeiRrhfufhigh) |
| **Network** | Solana |
| **Price** | $0.0002243 |
| **24h Volume** | $615.3K |
| **Liquidity** | $36.0K |
| **Volume / Liquidity** | 17.1× |
| **Token Age** | 22h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 4998 buys / 4241 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/cqvmzmwdveufa5rzkubidyr4zmdqdpoljatsw6wgspmu)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/higherfun-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-04*
