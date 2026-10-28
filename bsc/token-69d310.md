---
token: 币安使命
ticker: 币安使命
network: bsc
risk_score: 27
status: low
date: 2026-10-28
---

# 币安使命 (币安使命) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 27/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/token-69d310-bsc)

---

## Audit Summary

The FlapTaxTokenV3 is an EIP-1167 minimal clone implementation of an ERC-20 token with custom tax and migration logic. The contract ownership has been renounced, effectively locking the privileged migration functions and ensuring the current state is immutable. The architecture follows standard OpenZeppelin upgradeable patterns, though the clone deployment makes it non-upgradeable in practice. No critical vulnerabilities were identified in the provided code map.

> **Final Recommendation:** The protocol is currently in a secure, immutable state due to the renounced ownership. No further action is required for the current deployment. 

Future deployments should ensure that if migration logic is intended to be used, ownership is only renounced after the final state has been verified and confirmed by the community or relevant stakeholders.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The contract utilizes standard, well-audited OpenZeppelin libraries for ERC-20 and EIP-712 functionality. The use of EIP-1167 minimal clones ensures a lightweight and predictable deployment… |
| **Governance / Economics** | 8/10 | Low | The economic model is fixed due to the renounced ownership. 7.4 Economic: The migration logic is now dormant, preventing any further changes to tax parameters. 7.5 Governance: Governance is… |
| **Upgrades** | 10/10 | Low | The contract is deployed as an EIP-1167 minimal clone, which is inherently immutable. 7.7 Upgrades: No upgrade path exists for the logic contract. 7.8 Operations: Operational risk is minimized by the… |

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

The ten largest holders own 68.7% of supply. Of that, 3.9% burned, 18.4% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 44.6% in wallets, 1.9% in other contracts. 735 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

735 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $26K (DexScreener, all pools). 24h trading volume $115K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: 3% on buy, 3% on sell. Market: $26K of DEX liquidity across 2 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x3998...7777`](https://bscscan.com/address/0x39986fe54d858caac70c6c5253e8ce53fe7f7777) |
| **Network** | BNB Chain |
| **Price** | $0.00006813 |
| **24h Volume** | $94.3K |
| **Liquidity** | $25.7K |
| **Volume / Liquidity** | 3.7× |
| **Token Age** | 22h |
| **Top-10 Holders** | 68.7% of supply |
| **Buy / Sell Tax** | 3.0% / 3.0% |
| **24h Transactions** | 6097 buys / 625 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x6af97c6147e5154e4612ade43f82087de23be12f)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/token-69d310-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-28*
