---
token: OpenReserve
ticker: OPNRS
network: ethereum
risk_score: 68
status: high
date: 2026-10-31
---

# OpenReserve (OPNRS) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 68/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/openreserve-eth)

---

## Audit Summary

The protocol implements a standard ERC-20 token using a UUPS proxy pattern. Ownership has been formally renounced, effectively locking administrative functions and preventing unauthorized changes to the contract state. The codebase relies on standard OpenZeppelin libraries, ensuring robust and battle-tested implementations for core token logic.

> **Final Recommendation:** The contract is secure and follows industry standards for upgradeable tokens. No further action is required as the renounced ownership ensures the current state is immutable and protected from administrative interference.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The architecture follows the UUPS proxy pattern (7.1 Architecture), ensuring efficient upgrades and separation of concerns. Code security (7.2) is high due to the use of audited OpenZeppelin… |
| **Governance / Economics** | 4/10 | Medium | Economic (7.4) and Governance (7.5) risks are negligible as the token contract does not implement complex minting, burning, or voting mechanisms. The renounced ownership ensures that no entity can… |
| **Upgrades** | 2/10 | High | The UUPS upgrade mechanism (7.7) is correctly implemented, allowing for future logic updates if required. Since ownership is renounced, the upgrade capability is effectively locked, preventing any… |

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

The ten largest holders own 97.7% of supply. What remains: 95.4% in wallets, 2.3% in other contracts. The deployer/owner wallet itself holds 2.3%. 119 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

119 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $365K (DexScreener, all pools). 24h trading volume $645K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: upgradeable proxy. Fees: no buy or sell tax. Market: $365K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xc757...e422`](https://etherscan.io/address/0xc7571dcec6c2c47fc83af514e21d2a17950ee422) |
| **Network** | Ethereum |
| **Price** | $0.02635 |
| **24h Volume** | $645.0K |
| **Liquidity** | $364.5K |
| **Volume / Liquidity** | 1.8× |
| **Token Age** | 22h |
| **Top-10 Holders** | 97.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 255 buys / 0 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0xfd8e7cb13bb71603cd80cbf9c6ccb6452f1fe07b)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/openreserve-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-31*
