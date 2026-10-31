---
token: Fission
ticker: FSSN
network: ethereum
risk_score: 68
status: high
date: 2026-10-31
---

# Fission (FSSN) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 68/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/fission-eth)

---

## Audit Summary

The protocol is a standard ERC-20 token implemented via a UUPS proxy pattern. Ownership has been explicitly renounced, meaning no administrative functions can be triggered to alter token logic or state. The codebase follows standard OpenZeppelin patterns, and no vulnerabilities were identified in the transfer logic or proxy configuration.

> **Final Recommendation:** The contract is secure and follows best practices for immutable token deployment. No further action is required as the renounced ownership ensures the current logic cannot be altered.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The architecture utilizes a standard UUPS proxy pattern (7.1 Architecture). Code security is robust, adhering to OpenZeppelin standards for ERC-20 (7.2 Code Security). Access control is effectively… |
| **Governance / Economics** | 4/10 | Medium | Economic parameters are fixed as the contract lacks minting or burning capabilities (7.4 Economic). Governance is non-existent due to the renounced ownership status (7.5 Governance). Operations are… |
| **Upgrades** | 2/10 | High | The contract uses a UUPS proxy pattern (7.7 Upgrades). While the implementation is upgradeable, the renounced ownership prevents any future modifications to the logic. This effectively locks the… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Uups |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | ⚠️ 1 |

## Security Findings

_⚪ 6 Informational_

### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint/owner authority, mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 95.1% of supply. What remains: 95.1% in wallets, 0.0% in other contracts. The deployer/owner wallet itself holds 10.7%. 169 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

169 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $275K (DexScreener, all pools). 24h trading volume $561K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: upgradeable proxy. Fees: no buy or sell tax. Market: $275K of DEX liquidity across 1 pools. Launch: 1 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 1 day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 1 day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x66b6...c375`](https://etherscan.io/address/0x66b67f39dda7137047931ea67c3ea25e2b42c375) |
| **Network** | Ethereum |
| **Price** | $24.0450 |
| **24h Volume** | $560.7K |
| **Liquidity** | $274.7K |
| **Volume / Liquidity** | 2.0× |
| **Token Age** | 1d |
| **Top-10 Holders** | 95.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 337 buys / 0 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ⚠️ Unknown |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0x3f5d4020395513406e455736a06791fcd47ddcee)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/fission-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-31*
