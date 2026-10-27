---
token: CL Ai Agent
ticker: 财来
network: bsc
risk_score: 2
status: low
date: 2026-10-27
---

# CL Ai Agent (财来) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 2/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/cl-ai-agent-bsc)

---

## Audit Summary

The FlapTaxTokenV3 is a minimal clone (EIP-1167) of a tax-enabled ERC-20 token. The contract ownership has been renounced, effectively disabling all privileged administrative functions. The architecture is immutable, and the token logic is locked. No vulnerabilities were identified in the current state.

> **Final Recommendation:** The contract is in a secure, finalized state. No further action is required as the administrative functions are permanently disabled. Users should continue to monitor the token's tax logic as defined in the immutable state.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The contract utilizes standard OpenZeppelin upgradeable patterns adapted for minimal clones. 7.1 Architecture is robust due to the immutable nature of the EIP-1167 proxy. 7.2 Code Security is high… |
| **Governance / Economics** | 10/10 | Low | 7.4 Economic and 7.5 Governance risks are non-existent as the contract is now decentralized and immutable. The migration functions, which previously allowed for tax adjustments, are now dormant. No… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not possible for this contract. As a minimal clone, the implementation address is hardcoded into the bytecode. This ensures long-term stability and prevents rug-pulls via logic… |

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

The ten largest holders own 92.9% of supply. Of that, 80.0% locked, 2.5% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 10.0% in wallets, 0.4% in other contracts. 1,040 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

1,040 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $167K (DexScreener, all pools). 24h trading volume $301K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: 3% on buy, 3% on sell. Market: $167K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x5165...7777`](https://bscscan.com/address/0x51651ffcee5a33a7a5e9cd8397d03c7f30e17777) |
| **Network** | BNB Chain |
| **Price** | $0.003469 |
| **24h Volume** | $300.6K |
| **Liquidity** | $167.3K |
| **Volume / Liquidity** | 1.8× |
| **Token Age** | 2h |
| **Top-10 Holders** | 92.9% of supply |
| **Buy / Sell Tax** | 3.0% / 3.0% |
| **24h Transactions** | 949 buys / 787 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x22971bb3486338619fe3adf74889e8dfad8c249d)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/cl-ai-agent-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-27*
