---
token: Entendre Finance
ticker: ENDFI
network: arbitrum
risk_score: 75
status: high
date: 2026-10-15
---

# Entendre Finance (ENDFI) — Smart Contract Security Analysis | Arbitrum

> **Risk Score: 75/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/entendre-finance-arb)

---

## Audit Summary

This report is based on an audit request for the contract at 0xf3e4788407151f02a0d009a10527d123e65e9af4 on Arbitrum. Due to the absence of provided source code, a comprehensive security assessment for specific vulnerabilities could not be performed. The risk levels and findings presented are generalized best practices and do not reflect a deep analysis of the contract's specific implementation.

> **Final Recommendation:** For any smart contract deployment, it is crucial to ensure that the source code is publicly verified and available on block explorers. This transparency allows for community review and independent security audits. Additionally, comprehensive testing, including unit, integration, and fuzz testing, should be conducted prior to deployment to mitigate potential vulnerabilities. Implement robust access control and consider a multi-signature setup for critical operations.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | Without access to the contract's source code, a detailed technical analysis of its architecture (7.1), code security (7.2), and access control mechanisms (7.3) is not possible. Therefore, no specific… |
| **Governance / Economics** | 1/10 | High | The economic model (7.4) and governance structure (7.5) of the contract cannot be evaluated without the underlying source code and protocol documentation. This prevents assessment of potential… |
| **Upgrades** | 6/10 | Medium | The contract's upgradeability features (7.7) and operational procedures (7.8) cannot be determined without source code analysis. It is unknown if the contract is upgradeable, and if so, what proxy… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 99.8% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 1 Medium · ⚪ 9 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 2 address(es) other than the owner/deployer. One of them — a wallet, 0x3de3…0215 — holds 99.8% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `I-01` — Lack of Verified Source Code  *(Severity: Informational · Status: Unresolved)*

The source code for the contract at 0xf3e4788407151f02a0d009a10527d123e65e9af4 is not publicly verified on the Arbitrum block explorer. This significantly hinders transparency and the ability for independent security analysis, impacting overall code security (7.2).

**Recommendation:** Verify and publish the contract's source code on the block explorer to enable public scrutiny and enhance trust in the contract's operations.


### `I-02` — Importance of Comprehensive Testing  *(Severity: Informational · Status: Unresolved)*

Without source code, it's impossible to confirm the extent of testing performed. Inadequate testing can lead to undiscovered vulnerabilities, impacting code security (7.2) and economic stability (7.4) of the protocol.

**Recommendation:** Ensure all smart contracts undergo rigorous and comprehensive testing, including unit tests, integration tests, and property-based/fuzz testing, covering all possible execution paths and edge cases.


### `I-03` — Best Practices for Access Control  *(Severity: Informational · Status: Unresolved)*

Access control (7.3) is a critical component of smart contract security. Without source code, it's impossible to verify if appropriate role-based access control or multi-signature mechanisms are implemented for sensitive functions, potentially leading to unauthorized actions.

**Recommendation:** Implement granular access control mechanisms, preferably using a multi-signature wallet for critical administrative functions, to prevent single points of failure and unauthorized operations.


### `I-04` — Event Emission for Transparency and Off-chain Monitoring  *(Severity: Informational · Status: Unresolved)*

Proper event emission is crucial for off-chain monitoring, user interface updates, and transparent operations (7.8). Without source code, it's unknown if all state-changing operations emit relevant events, which can hinder auditing and user experience.

**Recommendation:** Ensure all significant state changes and critical actions within the contract emit clear and informative events. This aids in off-chain indexing, auditing, and provides transparency to users.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 80.5% of supply. What remains: 80.5% in wallets, 0.0% in other contracts. The deployer/owner wallet itself holds 5.5%. 2,242 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

2,242 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $77K (DexScreener, all pools). 24h trading volume $128K (DexScreener, all pools).

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
| **Contract** | [`0xf3e4...9af4`](https://arbiscan.io/address/0xf3e4788407151f02a0d009a10527d123e65e9af4) |
| **Network** | Arbitrum |
| **Price** | $0.0167 |
| **24h Volume** | $128.0K |
| **Liquidity** | $76.6K |
| **Volume / Liquidity** | 1.7× |
| **Token Age** | 1d |
| **Top-10 Holders** | 80.5% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 791 buys / 70 sells |

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

- [View on DexScreener](https://dexscreener.com/arbitrum/0x380b4451d7e3757626ec632af835b08e60af70c0)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/entendre-finance-arb)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-15*
