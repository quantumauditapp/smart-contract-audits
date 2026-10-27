---
token: Agent City
ticker: AGENT CITY
network: bsc
risk_score: 40
status: medium
date: 2026-10-27
---

# Agent City (AGENT CITY) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 40/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/agent-city-bsc)

---

## Audit Summary

The FlapTaxTokenV3 is an EIP-1167 minimal clone implementation. The contract ownership has been renounced, effectively locking the administrative functions. The architecture is immutable, and the token follows standard ERC-20 patterns with additional tax-enforcement logic.

> **Final Recommendation:** No security issues were identified. As the contract ownership is renounced and the architecture is immutable, the protocol is in a stable, finalized state. No further action is required for the current implementation.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes a robust EIP-1167 minimal clone pattern, ensuring consistent logic across deployments. 7.1 Architecture is sound, utilizing standard OpenZeppelin upgradeable base contracts for… |
| **Governance / Economics** | 6/10 | Medium | 7.4 Economic and 7.5 Governance parameters are locked due to the renounced ownership. The token logic includes tax-enforcement mechanisms that are now immutable. 7.6 External dependencies are limited… |
| **Upgrades** | 8/10 | Low | 7.7 Upgrades are not possible for this contract as it is an EIP-1167 minimal clone. The implementation is fixed at deployment, providing high security against proxy-based upgrade attacks. 7.8… |

## Security Findings

_🟠 1 High · ⚪ 5 Informational_

### `QA-HOLDERS` — Who holds the supply  *(Severity: High · Status: Acknowledged)*

The ten largest holders own 59.6% of supply. What remains: 12.9% in wallets, 46.6% in other contracts. The deployer/owner wallet itself holds 34.6%. A holder that also controls the contract can sell into its own liquidity. 163 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint/owner authority, mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

163 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $19K (DexScreener, all pools). 24h trading volume $66K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $19K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xb27d...7777`](https://bscscan.com/address/0xb27d4b9361c2eb84a6f8537c6f852115e0f77777) |
| **Network** | BNB Chain |
| **Price** | $0.00002041 |
| **24h Volume** | $65.7K |
| **Liquidity** | $19.3K |
| **Volume / Liquidity** | 3.4× |
| **Token Age** | 1h |
| **Top-10 Holders** | 59.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 880 buys / 580 sells |

## Security Flags (4/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ⚠️ Unknown |
| Not Upgradeable | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| Not Upgradeable | ✅ | Minimal proxy clone — the implementation is fixed in its bytecode and cannot be swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x9452305fab215df45c08167519a3c59ccaa1a695)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/agent-city-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-27*
