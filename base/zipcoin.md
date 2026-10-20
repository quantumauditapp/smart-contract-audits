---
token: zipcoin
ticker: ZC
network: base
risk_score: 83
status: high
date: 2026-10-02
---

# zipcoin (ZC) — Smart Contract Security Analysis | Base

> **Risk Score: 83/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/zipcoin-base)

---

## Audit Summary

This report is based on an audit request for contract 0x0f43374670bd7533cdb9d0b9d8294a8820350389 on the Base network. No source code was provided for analysis, therefore a comprehensive security assessment could not be performed. The risk levels and findings are placeholders reflecting the lack of information and the inherent risk of interacting with unverified contracts.

> **Final Recommendation:** To enable a thorough security audit, it is crucial to provide the complete and verified source code for the contract. Without source code, no specific security recommendations can be offered, and the contract's security posture remains unknown. Users should exercise extreme caution when interacting with unverified contracts, as they may contain critical vulnerabilities.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | Without access to the contract's source code, a detailed technical security analysis (7.1 Architecture, 7.2 Code Security, 7.3 Access Control) cannot be conducted. Potential vulnerabilities such as… |
| **Governance / Economics** | 1/10 | High | The economic and governance aspects (7.4 Economic, 7.5 Governance) of the contract cannot be evaluated without the underlying source code. This prevents assessment of tokenomics, fee structures… |
| **Upgrades** | 5/10 | Medium | The upgradeability model (7.7 Upgrades) of the contract cannot be determined without the source code. It is unknown if the contract is upgradeable, what proxy pattern it might use, or if there are… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 99.6% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · ⚪ 9 Informational_

### `QA-LIQUIDITY` — Liquidity withdrawable by the owner/deployer  *(Severity: High · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 99.6% is held, unlocked, by the token's owner/deployer (0x218e…04e2) — they can pull that liquidity at any moment. This is the rug-pull path. 0.4% is held, unlocked, by 1 address(es) other than the owner/deployer. No single one holds a majority: their exits thin the market rather than hand anyone the pool.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `I-01` — No Source Code Provided for Analysis  *(Severity: Informational · Status: Unresolved)*

The audit request did not include the source code for the contract at 0x0f43374670bd7533cdb9d0b9d8294a8820350389. This prevents any form of static or dynamic analysis.

**Recommendation:** Provide the complete and verified Solidity source code for the contract to enable a comprehensive security audit.


### `I-02` — Inability to Assess Technical Security  *(Severity: Informational · Status: Unresolved)*

Without the contract's source code, it is impossible to assess technical security aspects such as reentrancy, integer overflows/underflows, access control flaws, logic errors, or gas optimizations (7.2 Code Security, 7.3 Access Control).

**Recommendation:** Submit the contract's source code for a detailed technical security review.


### `I-03` — Inability to Assess Economic and Governance Risks  *(Severity: Informational · Status: Unresolved)*

The absence of source code prevents the evaluation of economic models, governance mechanisms, oracle dependencies, or potential for flash loan attacks (7.4 Economic, 7.5 Governance).

**Recommendation:** Provide the source code to allow for an assessment of economic and governance risks.


### `I-04` — Inability to Assess Upgradeability and Operational Risks  *(Severity: Informational · Status: Unresolved)*

Without source code, it is impossible to determine if the contract is upgradeable, what proxy pattern is used, or to assess any upgrade safety issues (7.7 Upgrades). Operational risks (7.8 Operations) related to administrative functions or emergency procedures also cannot be evaluated.

**Recommendation:** Submit the contract's source code to enable a review of its upgradeability and operational aspects.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 40.7% of supply. Of that, 15.6% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 25.1% in wallets, 0.0% in other contracts. 1,104 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

1,104 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $232K (DexScreener, all pools). 24h trading volume $585K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mint capability could not be read. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $232K of DEX liquidity across 1 pools. Launch: 2 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 2 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 2 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x0f43...0389`](https://basescan.org/address/0x0f43374670bd7533cdb9d0b9d8294a8820350389) |
| **Network** | Base |
| **Price** | $0.00000077 |
| **24h Volume** | $585.2K |
| **Liquidity** | $231.8K |
| **Volume / Liquidity** | 2.5× |
| **Token Age** | 2d |
| **Top-10 Holders** | 40.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 269 buys / 241 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0x54d5a55d4e870a03d82866c57150ed5458c8f9dd)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/zipcoin-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-02*
