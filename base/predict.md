---
token: Predict
ticker: PREDICT
network: base
risk_score: 33
status: low
date: 2026-10-28
---

# Predict (PREDICT) — Smart Contract Security Analysis | Base

> **Risk Score: 33/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/predict-base)

---

## Audit Summary

The BaseToken contract is a standard ERC-20 implementation with burnable capabilities. Ownership has been formally renounced, meaning no administrative functions can be executed, effectively locking the contract configuration. The codebase relies on well-vetted OpenZeppelin libraries, ensuring standard compliance and robust security posture.

> **Final Recommendation:** The contract is secure and requires no further action. As ownership is renounced, the current state is permanent and immutable.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The architecture follows standard ERC-20 patterns using established OpenZeppelin libraries for 7.1 Architecture and 7.2 Code Security. 7.3 Access Control is effectively disabled due to ownership… |
| **Governance / Economics** | 7/10 | Low | 7.4 Economic and 7.5 Governance parameters are immutable as ownership is renounced. There are no inflationary mechanisms or complex reward structures that could be manipulated. The token functions… |
| **Upgrades** | 9/10 | Low | The contract is not a proxy, so 7.7 Upgrades are not applicable. 7.8 Operations are stable and require no ongoing maintenance or administrative intervention. |

## Security Findings

_🟠 1 High · ⚪ 5 Informational_

### `QA-HOLDERS` — Who holds the supply  *(Severity: High · Status: Acknowledged)*

The ten largest holders own 46.7% of supply. What remains: 46.7% in wallets, 0.0% in other contracts. The deployer/owner wallet itself holds 41.0%. A holder that also controls the contract can sell into its own liquidity. 526 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint/owner authority, mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

526 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $92K (DexScreener, all pools). 24h trading volume $863K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $92K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x14a5...7245`](https://basescan.org/address/0x14a521e399667532f0d7b5413f725766e32f7245) |
| **Network** | Base |
| **Price** | $0.0001411 |
| **24h Volume** | $863.0K |
| **Liquidity** | $92.0K |
| **Volume / Liquidity** | 9.4× |
| **Token Age** | 14h |
| **Top-10 Holders** | 46.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1194 buys / 929 sells |

## Security Flags (4/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ⚠️ Unknown |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/base/0xb30292cd89227d1b70900e8a71b9894d2b32bf1c6dc0f56d34d1f49a87412ecc)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/predict-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-28*
