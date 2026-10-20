---
token: Eunice
ticker: EUIAI
network: arbitrum
risk_score: 74
status: high
date: 2026-10-05
---

# Eunice (EUIAI) — Smart Contract Security Analysis | Arbitrum

> **Risk Score: 74/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/eunice-arb)

---

## Audit Summary

This report is based on an audit request for the contract at 0x171f70d6f5b843d7656436af1abdfd646bca6d7c on Arbitrum. No source code was provided for analysis, which severely limits the scope and depth of this security assessment. Therefore, no specific vulnerabilities or strengths could be identified within the contract's logic. The risk levels are set to 'Low' by default due to the absence of findings, but this does not imply the contract is secure.

> **Final Recommendation:** To conduct a meaningful security audit, it is imperative to provide the complete and verified source code for the contract. Without source code, no specific vulnerabilities can be identified, and no assurances regarding the contract's security can be made. It is strongly recommended to publish the source code on block explorers and ensure it matches the deployed bytecode.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | Due to the absence of source code, a comprehensive technical security analysis (7.1 Architecture, 7.2 Code Security, 7.3 Access Control) could not be performed. No specific code patterns… |
| **Governance / Economics** | 1/10 | High | Without access to the contract's source code, it is impossible to assess economic models (7.4 Economic), governance structures (7.5 Governance), or external dependencies (7.6 External). Key aspects… |
| **Upgrades** | 6/10 | Medium | The upgradeability status (7.7 Upgrades) and operational procedures (7.8 Operations) of the contract cannot be determined without its source code. It is unknown if the contract implements a proxy… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 99.9% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 1 Medium · ⚪ 8 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 2 address(es) other than the owner/deployer. One of them — a wallet, 0x59bd…3685 — holds 99.9% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `I-01` — No Source Code Provided for Audit  *(Severity: Informational · Status: Unresolved)*

The primary limitation of this audit is the absence of the contract's source code. Without the Solidity code, a comprehensive security analysis cannot be performed. This prevents the identification of common vulnerabilities such as reentrancy, integer overflows, access control flaws, or logical errors.

**Recommendation:** To enable a thorough security audit, the complete and verified source code for the contract at 0x171f70d6f5b843d7656436af1abdfd646bca6d7c must be provided. It is best practice to verify the source code on block explorers like Arbiscan.


### `I-02` — Inability to Assess Technical Security  *(Severity: Informational · Status: Unresolved)*

Due to the lack of source code, it was impossible to evaluate the contract's technical security aspects, including its architecture (7.1), code security (7.2), and access control mechanisms (7.3). This means no assessment of potential reentrancy vectors, arithmetic safety, or privilege separation could be made.

**Recommendation:** Provide the source code to allow for a detailed review of the contract's technical implementation, including its design patterns, security best practices, and access control logic. This is crucial for identifying and mitigating technical vulnerabilities.


### `I-03` — Inability to Assess Economic, Governance, and Upgrade Risks  *(Severity: Informational · Status: Unresolved)*

Without the contract's source code, it is not possible to analyze its economic model (7.4), governance structure (7.5), external dependencies (7.6), upgradeability (7.7), or operational procedures (7.8). Key risks related to tokenomics, administrative control, oracle manipulation, or upgrade path safety remain unassessed.

**Recommendation:** Submit the source code to enable a full audit scope, covering economic incentives, governance mechanisms, external interactions, and upgrade strategies. This will allow for a holistic risk assessment beyond just code-level vulnerabilities.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 83.5% of supply. Of that, 3.5% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 80.1% in wallets, 0.0% in other contracts. The deployer/owner wallet itself holds 8.3%. 2,228 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

2,228 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $77K (DexScreener, all pools). 24h trading volume $103K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mint capability could not be read. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $77K of DEX liquidity across 1 pools. Launch: 1 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 1 day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 1 day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x171f...6d7c`](https://arbiscan.io/address/0x171f70d6f5b843d7656436af1abdfd646bca6d7c) |
| **Network** | Arbitrum |
| **Price** | $0.0111 |
| **24h Volume** | $103.1K |
| **Liquidity** | $76.6K |
| **Volume / Liquidity** | 1.3× |
| **Token Age** | 1d |
| **Top-10 Holders** | 83.5% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 676 buys / 55 sells |

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

- [View on DexScreener](https://dexscreener.com/arbitrum/0x62e158d97d0af1e9e1bd5bbcbe2b416e5bd65ff5)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/eunice-arb)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-05*
