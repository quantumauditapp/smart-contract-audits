---
token: 币安支付
ticker: BINANCE PAY
network: bsc
risk_score: 17
status: low
date: 2026-10-21
---

# 币安支付 (BINANCE PAY) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 17/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/binance-pay-bsc)

---

## Audit Summary

The FlapTaxTokenV3 is a minimal clone implementation of an ERC-20 token with custom migration and tax logic. The contract ownership has been renounced, effectively disabling the privileged migration functions. The architecture is immutable, and the code follows standard OpenZeppelin patterns for upgradeable contracts, though the clone pattern prevents future logic changes.

> **Final Recommendation:** The contract is secure due to the renounced ownership and immutable clone architecture. No further action is required as the privileged functions are dormant and the logic is fixed.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The contract utilizes a robust EIP-1167 minimal clone architecture, ensuring low deployment costs and consistent logic. 7.1 Architecture: The design is modular and follows standard ERC-20 compliance.… |
| **Governance / Economics** | 9/10 | Low | 7.4 Economic: The tokenomics are fixed by the immutable state of the clone. 7.5 Governance: Governance is effectively non-existent due to the renounced ownership. 7.6 External: The contract does not… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades: The contract is a minimal clone, meaning the logic is permanently fixed and cannot be upgraded. 7.8 Operations: Operational risk is minimal as the contract state is locked and… |

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

The ten largest holders own 49.5% of supply. Of that, 6.3% burned, 29.4% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 12.0% in wallets, 1.9% in other contracts. 19,494 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

19,494 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $20K (DexScreener, all pools). 24h trading volume $99K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: 2% on buy, 2% on sell. Market: $20K of DEX liquidity across 1 pools. Launch: 27 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 27 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 27 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xe4eb...7777`](https://bscscan.com/address/0xe4eb159e568ec18e565195de753410559e8d7777) |
| **Network** | BNB Chain |
| **Price** | $0.00004096 |
| **24h Volume** | $98.8K |
| **Liquidity** | $20.2K |
| **Volume / Liquidity** | 4.9× |
| **Token Age** | 27d |
| **Top-10 Holders** | 49.5% of supply |
| **Buy / Sell Tax** | 2.0% / 2.0% |
| **24h Transactions** | 3011 buys / 943 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x36dbf4526f1e14ff4c0a9071be6a6afc074e65d5)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/binance-pay-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-21*
