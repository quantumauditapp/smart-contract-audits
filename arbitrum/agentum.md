---
token: Agentum
ticker: AGT
network: arbitrum
risk_score: 76
status: high
date: 2026-09-30
---

# Agentum (AGT) — Smart Contract Security Analysis | Arbitrum

> **Risk Score: 76/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/agentum-arb)

---

## Audit Summary

No Solidity source code was provided for analysis. This report reflects a theoretical assessment based on the absence of code, and no specific vulnerabilities could be identified or verified. A comprehensive security audit requires full access to the contract's implementation.

> **Final Recommendation:** To ensure the security and integrity of the contract at 0xa83d9739dff70b44f44c2d94bd24d80bd9225031, it is crucial to provide the complete and verified Solidity source code. A comprehensive audit can only be performed once the code is available for review, allowing for the identification and mitigation of potential vulnerabilities. Public verification of the source code on block explorers is highly recommended for transparency.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | No Solidity source code was provided for technical analysis. Therefore, no assessment of architecture (7.1), code security (7.2), or access control (7.3) could be performed. Without code, it is… |
| **Governance / Economics** | 1/10 | High | Without access to the contract's source code, an evaluation of economic mechanisms (7.4) and governance structures (7.5) is not possible. Potential risks such as oracle manipulation, economic… |
| **Upgrades** | 5/10 | Medium | No source code was provided, preventing an assessment of upgradeability patterns (7.7) or potential upgrade safety issues. Operational aspects (7.8) and external dependencies (7.6) also remain… |

## Security Findings

_⚪ 6 Informational_

### `I-01` — Missing Source Code for Analysis  *(Severity: Informational · Status: Unresolved)*

The Solidity source code for the contract at address 0xa83d9739dff70b44f44c2d94bd24d80bd9225031 was not provided. Without access to the contract's implementation details, a comprehensive security audit cannot be performed. This prevents the identification of specific vulnerabilities related to architecture (7.1), code security (7.2), access control (7.3), economic models (7.4), governance (7.5), external interactions (7.6), and upgrade mechanisms (7.7), and operational aspects (7.8).

**Recommendation:** Provide the complete and verified Solidity source code for the contract. It is highly recommended to verify the source code on block explorers (e.g., Arbiscan) to ensure transparency and allow for public scrutiny and security analysis.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 92.6% of supply. What remains: 92.6% in wallets, 0.0% in other contracts. The deployer/owner wallet itself holds 1.4%. 424 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

424 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $79K (DexScreener, all pools). 24h trading volume $181K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mint capability could not be read. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $79K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xa83d...5031`](https://arbiscan.io/address/0xa83d9739dff70b44f44c2d94bd24d80bd9225031) |
| **Network** | Arbitrum |
| **Price** | $0.1573 |
| **24h Volume** | $181.4K |
| **Liquidity** | $78.7K |
| **Volume / Liquidity** | 2.3× |
| **Token Age** | 23h |
| **Top-10 Holders** | 92.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1081 buys / 304 sells |

## Security Flags (1/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ❌ Fail |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ⚠️ Unknown |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ❌ | Source code is **not verified** — contract logic is opaque. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/arbitrum/0xcadab9b65ec5cba178725a1f4ccd38018822a453)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/agentum-arb)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-30*
