---
token: Catalyst
ticker: CALY
network: arbitrum
risk_score: 76
status: high
date: 2026-10-19
---

# Catalyst (CALY) — Smart Contract Security Analysis | Arbitrum

> **Risk Score: 76/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/catalyst-arb)

---

## Audit Summary

The provided contract text was empty, preventing a comprehensive source code audit. This report is based on the limited information available (address, network, verification status) and general security best practices for unverified contracts. The absence of source code significantly elevates all categories of risk.

> **Final Recommendation:** It is strongly recommended that the contract owner verify the source code on a public block explorer. This action is fundamental for transparency, user trust, and enabling any form of security assessment. Without verified source code, users should exercise extreme caution and avoid interacting with the contract, as its functionality and security properties remain entirely unknown and unauditable.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | A comprehensive technical security assessment (7.1 Architecture, 7.2 Code Security) was not possible due to the absence of verified source code. This lack of transparency prevents any analysis of… |
| **Governance / Economics** | 1/10 | High | The economic model and governance structure (7.4 Economic, 7.5 Governance) of the contract could not be assessed without source code. This means potential centralization risks, such as an owner… |
| **Upgrades** | 6/10 | Medium | The upgradeability status and safety (7.7 Upgrades) of the contract could not be determined without source code. It is unknown if the contract is part of a proxy pattern, and if so, whether the… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 99.9% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 2 High · 🟡 3 Medium · ⚪ 5 Informational_

### `H-01` — Lack of Verified Source Code  *(Severity: High · Status: Unresolved)*

The contract at `0x711eeadca53fb6665a87ac5ac7fedb5d6ceb4e82` on Arbitrum does not have verified source code on block explorers. This prevents a thorough security audit and makes it impossible for users to understand the contract's intended functionality and security properties. (7.2 Code Security, 7.8 Operations)

**Recommendation:** Verify the contract source code on a public block explorer (e.g., Arbiscan) to enable transparency and allow for public scrutiny and security analysis.


### `H-02` — Unknown Contract Functionality and Purpose  *(Severity: High · Status: Unresolved)*

Without verified source code, the exact functionality, purpose, and state-changing operations of the contract cannot be determined. This poses a significant risk as users interacting with the contract do so blindly, potentially exposing themselves to unexpected behavior, loss of funds, or unauthorized actions. (7.1 Architecture, 7.4 Economic)

**Recommendation:** Provide comprehensive documentation detailing the contract's architecture, intended use, and all external functions. This should accompany the verified source code.


### `M-01` — Elevated Operational Risk  *(Severity: Medium · Status: Unresolved)*

The absence of source code significantly increases operational risk. In the event of an incident, bug, or unexpected behavior, debugging, analysis, and incident response become extremely challenging or impossible without visibility into the contract's logic. (7.8 Operations)

**Recommendation:** Ensure that all deployed contracts have verified source code and are thoroughly documented to facilitate efficient operational management and incident response.


### `M-02` — Inability to Assess Access Control and Economic Model  *(Severity: Medium · Status: Unresolved)*

Without source code, it is impossible to assess the contract's access control mechanisms (e.g., owner privileges, role-based access) or its economic model (e.g., fee structures, tokenomics, incentive mechanisms). This means potential centralization risks, rug pull vectors, or economic exploits cannot be identified. (7.3 Access Control, 7.4 Economic, 7.5 Governance)

**Recommendation:** Implement robust, transparent access control mechanisms and a well-defined, publicly auditable economic model. Verification of source code is crucial for this assessment.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 2 address(es) other than the owner/deployer. One of them — a wallet, 0x35c2…7402 — holds 99.9% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 84.2% of supply. Of that, 4.2% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 79.9% in wallets, 0.0% in other contracts. The deployer/owner wallet itself holds 8.2%. 2,233 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

2,233 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $82K (DexScreener, all pools). 24h trading volume $97K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mint capability could not be read. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $82K of DEX liquidity across 1 pools. Launch: 1 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 1 day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 1 day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x711e...4e82`](https://arbiscan.io/address/0x711eeadca53fb6665a87ac5ac7fedb5d6ceb4e82) |
| **Network** | Arbitrum |
| **Price** | $0.009752 |
| **24h Volume** | $97.1K |
| **Liquidity** | $82.4K |
| **Volume / Liquidity** | 1.2× |
| **Token Age** | 1d |
| **Top-10 Holders** | 84.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 687 buys / 59 sells |

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

- [View on DexScreener](https://dexscreener.com/arbitrum/0x838313d4f269d83c5cda9d7104f27ccae739b98a)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/catalyst-arb)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-19*
