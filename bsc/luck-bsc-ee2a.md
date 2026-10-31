---
token: LUCK
ticker: LUCK
network: bsc
risk_score: 0
status: low
date: 2026-10-31
---

# LUCK (LUCK) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 0/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/luck-bsc-ee2a)

---

## Audit Summary

The FlapTaxTokenV3 is an EIP-1167 minimal clone implementation. The contract ownership has been renounced on-chain, effectively disabling all privileged administrative functions. The architecture is immutable, and the token logic is locked. No active vulnerabilities were identified in the current state.

> **Final Recommendation:** The protocol is in a secure, immutable state due to the renouncement of ownership. No further action is required for the current deployment as the administrative surface area is dormant.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The contract utilizes standard OpenZeppelin upgradeable libraries for ERC-20 and EIP-712 compliance. 7.1 Architecture: The EIP-1167 clone pattern ensures a lightweight, immutable deployment. 7.2 Code… |
| **Governance / Economics** | 10/10 | Low | 7.4 Economic: The token logic includes migration and tax enforcement states, but these are now locked due to ownership renouncement. 7.5 Governance: There is no active governance mechanism; the… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades: The contract is a minimal clone, which is inherently immutable and cannot be upgraded. 7.8 Operations: Operational risk is minimal as the contract state is fixed and cannot be altered… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Null Address |

## Security Findings

_⚪ 7 Informational_

### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint/owner authority, mint capability, LP lock/burn state, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 14.4% of supply. Of that, 1.3% burned, 6.6% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 5.0% in wallets, 1.5% in other contracts. 1,477 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

1,477 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $68K (DexScreener, all pools). 24h trading volume $39K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: 3.5% on buy, 3.5% on sell. Market: $68K of DEX liquidity across 1 pools. Launch: 1 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 1 day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 1 day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x11e3...7777`](https://bscscan.com/address/0x11e3ee544418a074679f9aa0dc77824207aa7777) |
| **Network** | BNB Chain |
| **Price** | $0.0005034 |
| **24h Volume** | $39.3K |
| **Liquidity** | $67.7K |
| **Volume / Liquidity** | 0.6× |
| **Token Age** | 1d |
| **Top-10 Holders** | 14.4% of supply |
| **Buy / Sell Tax** | 3.5% / 3.5% |
| **24h Transactions** | 262 buys / 212 sells |

## Security Flags (5/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ✅ Pass |
| Not Upgradeable | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not Upgradeable | ✅ | Minimal proxy clone — the implementation is fixed in its bytecode and cannot be swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0xb2d5d805729a4d0f5d9e0d4a92e39c0eaaf01076)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/luck-bsc-ee2a)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-31*
