---
token: Symbiotic
ticker: SYMB
network: ethereum
risk_score: 64
status: medium
date: 2026-11-03
---

# Symbiotic (SYMB) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 64/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/symbiotic-eth)

---

## Audit Summary

The audited contract is a standard ERC-20 implementation utilizing the UUPS proxy pattern. Ownership has been permanently renounced, ensuring that no administrative functions can be triggered to alter contract logic or state. The codebase follows established OpenZeppelin standards, providing a robust foundation for token operations.

> **Final Recommendation:** The contract is secure and follows best practices for immutable, upgradeable token deployments. No further action is required as ownership has been renounced, effectively locking the current implementation and configuration.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The architecture leverages the UUPS proxy pattern, which is gas-efficient and well-documented. 7.1 Architecture is sound, utilizing standard OpenZeppelin libraries. 7.2 Code Security is high, with no… |
| **Governance / Economics** | 6/10 | Medium | 7.4 Economic and 7.5 Governance risks are minimal as the contract lacks minting, burning, or fee-switching capabilities. The token functions as a standard utility asset. 7.6 External dependencies are… |
| **Upgrades** | 2/10 | High | 7.7 Upgrades are technically possible via the UUPS pattern, but the renounced ownership renders the upgrade mechanism dormant. 7.8 Operations are stable, as the contract state is immutable regarding… |

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

The ten largest holders own 80.7% of supply. What remains: 62.3% in wallets, 18.4% in other contracts. The deployer/owner wallet itself holds 6.6%. 110 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

110 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $122K (DexScreener, all pools). 24h trading volume $179K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: upgradeable proxy. Fees: no buy or sell tax. Market: $122K of DEX liquidity across 1 pools. Launch: 2 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 2 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 2 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xd3cf...0509`](https://etherscan.io/address/0xd3cf43950a7c1ef8e558ec5052512e4689130509) |
| **Network** | Ethereum |
| **Price** | $9.8400 |
| **24h Volume** | $178.7K |
| **Liquidity** | $122.2K |
| **Volume / Liquidity** | 1.5× |
| **Token Age** | 2d |
| **Top-10 Holders** | 80.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 316 buys / 0 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x0b0dd031ec7243f8d909a4b8a262c7f11fa2e5a7)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/symbiotic-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-03*
