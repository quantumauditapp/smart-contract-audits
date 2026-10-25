---
token: 100u and a Dream
ticker: 100U
network: bsc
risk_score: 22
status: low
date: 2026-10-25
---

# 100u and a Dream (100U) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 22/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/100u-and-a-dream-bsc)

---

## Audit Summary

The FlapTaxTokenV3 is a standard ERC-20 token implemented as an EIP-1167 minimal clone. The contract ownership has been renounced, effectively disabling all administrative functions that could modify the token's tax or migration state. The codebase is clean and adheres to standard OpenZeppelin patterns for upgradeable contracts, though the deployment architecture is immutable.

> **Final Recommendation:** The contract is secure and immutable. No further action is required as the renounced ownership prevents any further administrative changes to the token's tax or migration logic.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The contract utilizes standard ERC-20 and EIP-712 permit functionality with robust implementation. 7.1 Architecture: EIP-1167 clone pattern ensures minimal gas overhead. 7.2 Code Security: Logic is… |
| **Governance / Economics** | 7/10 | Low | 7.4 Economic: The token utilizes a tax-enforced mechanism that is now locked due to ownership renouncement. 7.5 Governance: No active governance exists as the owner role is nullified. 7.8 Operations… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades: The EIP-1167 minimal clone pattern is inherently immutable. The implementation address is fixed at deployment and cannot be changed. This eliminates risks associated with malicious… |

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

The ten largest holders own 40.5% of supply. Of that, 22.4% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 8.2% in wallets, 9.9% in other contracts. 614 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

614 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $22K (DexScreener, all pools). 24h trading volume $691K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: 0% on buy, 1% on sell. Market: $22K of DEX liquidity across 2 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xe4d6...7777`](https://bscscan.com/address/0xe4d6828aea884d456879019a054fd3efccb87777) |
| **Network** | BNB Chain |
| **Price** | $0.00004633 |
| **24h Volume** | $616.1K |
| **Liquidity** | $22.0K |
| **Volume / Liquidity** | 28.0× |
| **Token Age** | 6h |
| **Top-10 Holders** | 40.5% of supply |
| **Buy / Sell Tax** | 0.0% / 1.0% |
| **24h Transactions** | 4724 buys / 3854 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x2b1f40ee91fc35b09a1b6522331d9620f8cde3ff)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/100u-and-a-dream-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-25*
