---
token: Orthogonal
ticker: ORTGO
network: arbitrum
risk_score: 69
status: high
date: 2026-10-07
---

# Orthogonal (ORTGO) — Smart Contract Security Analysis | Arbitrum

> **Risk Score: 69/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/orthogonal-arb-ef38)

---

## Audit Summary

No contract source code was provided for analysis. Therefore, a comprehensive security audit could not be performed. The report reflects general security best practices and informational findings regarding the importance of source code availability for a thorough assessment.

> **Final Recommendation:** For any smart contract deployment, it is paramount to provide verified source code. This enables comprehensive security audits, fosters transparency, and builds trust within the community. Projects should prioritize making their code publicly available and undergoing thorough audits by reputable firms before deployment to identify and mitigate potential vulnerabilities. Additionally, robust testing, formal verification, and a clear incident response plan are crucial for long-term security.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | Without access to the contract's source code, a detailed technical security assessment (7.1 Architecture, 7.2 Code Security, 7.3 Access Control) cannot be conducted. General best practices for EVM… |
| **Governance / Economics** | 1/10 | High | The economic and governance aspects (7.4 Economic, 7.5 Governance) of the contract cannot be assessed without source code. Key considerations typically include tokenomics, fee structures, and… |
| **Upgrades** | 6/10 | Medium | Upgradeability mechanisms (7.7 Upgrades) and their associated risks cannot be determined without the contract's source code. Proxy patterns (e.g., UUPS, Transparent) introduce specific upgrade safety… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 99.8% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 1 Medium · ⚪ 8 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 2 address(es) other than the owner/deployer. One of them — a wallet, 0xce1f…a2cf — holds 99.8% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `I-01` — Missing Source Code for Comprehensive Audit  *(Severity: Informational · Status: Unresolved)*

The source code for the contract at 0x868a6ce274eeb011ac10822a8d6401f018ae9d1f was not provided. This prevents a thorough security audit, including analysis of architectural design (7.1 Architecture), code-level vulnerabilities (7.2 Code Security), and specific access control mechanisms (7.3 Access Control).

**Recommendation:** Always provide verified source code for all deployed contracts. This allows for a complete security assessment, enhances transparency, and enables the community to verify the contract's intended behavior.


### `I-02` — Inability to Verify Security Best Practices  *(Severity: Informational · Status: Unresolved)*

Without source code, it is impossible to verify if standard security best practices, such as reentrancy guards, integer overflow/underflow protections, proper event emission, and secure handling of external calls (7.6 External), have been implemented. This leaves potential unknown vulnerabilities unaddressed.

**Recommendation:** Ensure all smart contracts adhere to established security best practices. Implement robust testing, including unit, integration, and fuzz testing, to validate the correctness and security of the code. Utilize secure development patterns and libraries.


### `I-03` — Lack of Transparency and Trust  *(Severity: Informational · Status: Unresolved)*

The absence of publicly available and verified source code for a deployed contract significantly reduces transparency and trust for users and the broader ecosystem. It prevents independent verification of the contract's logic, economic model (7.4 Economic), and governance structure (7.5 Governance), raising concerns about hidden functionalities or potential backdoors.

**Recommendation:** Publish and verify the source code for all deployed contracts on block explorers (e.g., Etherscan, Arbiscan). This promotes transparency, allows for community scrutiny, and builds confidence in the project's integrity and security posture.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 78.9% of supply. What remains: 50.9% in wallets, 28.0% in other contracts. The deployer/owner wallet itself holds 7.2%. 2,240 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

2,240 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $74K (DexScreener, all pools). 24h trading volume $148K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mint capability could not be read. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $74K of DEX liquidity across 1 pools. Launch: 1 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 1 day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 1 day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x868a...9d1f`](https://arbiscan.io/address/0x868a6ce274eeb011ac10822a8d6401f018ae9d1f) |
| **Network** | Arbitrum |
| **Price** | $0.01902 |
| **24h Volume** | $147.9K |
| **Liquidity** | $74.4K |
| **Volume / Liquidity** | 2.0× |
| **Token Age** | 1d |
| **Top-10 Holders** | 78.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 715 buys / 72 sells |

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

- [View on DexScreener](https://dexscreener.com/arbitrum/0x7d134195e8e69faab370a29b0d7b63d430cfab77)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/orthogonal-arb-ef38)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-07*
