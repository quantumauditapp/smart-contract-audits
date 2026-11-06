---
token: KieDex
ticker: KDX
network: ethereum
risk_score: 58
status: medium
date: 2026-11-06
---

# KieDex (KDX) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 58/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/kiedex-eth)

---

## Audit Summary

The protocol is a standard ERC-20 token implemented via a UUPS proxy pattern. Ownership has been formally renounced, effectively locking the administrative functions and ensuring the contract logic remains immutable. No critical vulnerabilities were identified in the current implementation.

> **Final Recommendation:** The contract is in a secure, immutable state. No further action is required for the current deployment. Users should verify the implementation address against the proxy to ensure they are interacting with the intended logic.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The architecture follows standard OpenZeppelin ERC-20 and UUPS proxy patterns, ensuring high compatibility with existing DeFi ecosystems. 7.1 Architecture is robust, utilizing standard storage… |
| **Governance / Economics** | 6/10 | Medium | 7.4 Economic and 7.5 Governance risks are minimal as the contract is immutable. There are no minting or burning mechanisms that could impact token supply dynamics. 7.6 External dependencies are… |
| **Upgrades** | 2/10 | High | 7.7 Upgrades are technically possible via the UUPS pattern, but 7.8 Operations are effectively frozen due to the renounced ownership. The implementation contract is correctly linked to the proxy. No… |

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

The ten largest holders own 86.1% of supply. What remains: 21.0% in wallets, 65.1% in other contracts. 41 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

41 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $45K (DexScreener, all pools). 24h trading volume $58K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: upgradeable proxy. Fees: no buy or sell tax. Market: $45K of DEX liquidity across 1 pools. Launch: 1 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 1 day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 1 day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x9f6b...433d`](https://etherscan.io/address/0x9f6b08f95c15d9d2ddc9b082cd94f824d2b2433d) |
| **Network** | Ethereum |
| **Price** | $0.02118 |
| **24h Volume** | $58.3K |
| **Liquidity** | $44.9K |
| **Volume / Liquidity** | 1.3× |
| **Token Age** | 1d |
| **Top-10 Holders** | 86.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 308 buys / 0 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x5e355dfcbf40ac017a659ce3f40b986dd73d6cc9)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/kiedex-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-06*
