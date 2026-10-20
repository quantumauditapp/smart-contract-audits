---
token: ODEI AI
ticker: ODAI
network: base
risk_score: 38
status: medium
date: 2026-09-23
---

# ODEI AI (ODAI) — Smart Contract Security Analysis | Base

> **Risk Score: 38/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/odei-ai-base)

---

## Audit Summary

The Memecoin contract, serving as an upgradeable ERC20 token, demonstrates a solid foundation built upon OpenZeppelin's battle-tested libraries and Solidity 0.8+. It integrates cross-chain functionality and ERC20Votes for potential governance. However, the contract exhibits significant centralization risks due to its heavy reliance on the Flaunch contract for critical functions like minting and metadata management. The audit also identified a design choice regarding irreversible infinite allowance for Permit2 and noted the incomplete Flaunch contract code, which limits a full assessment of external dependencies.

> **Final Recommendation:** Prioritize a comprehensive audit of the `Flaunch` contract, as its security directly impacts the `Memecoin`'s integrity and economic model. Implement robust access control mechanisms and multi-signature wallets for critical `Flaunch` operations to mitigate the risks associated with centralized control over token supply and metadata. For the `Memecoin` contract, ensure that all future upgrades adhere strictly to proxy best practices, including meticulous storage slot management and thorough testing to prevent re-initialization vulnerabilities or unintended state changes.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 7/10 | Low | The Memecoin contract demonstrates robust technical foundations, leveraging battle-tested OpenZeppelin upgradeable contracts and Solidity 0.8+ for arithmetic safety (7.2 Code Security). It integrates… |
| **Governance / Economics** | 6/10 | Medium | The Memecoin contract incorporates `ERC20VotesUpgradeable`, enabling potential on-chain governance mechanisms and automatic delegation upon transfer, which is a positive for decentralized control… |
| **Upgrades** | 6/10 | Medium | The contract is designed as an upgradeable proxy using OpenZeppelin's `Initializable` pattern, ensuring a secure upgrade path (7.7 Upgrades). The `_disableInitializers` in the constructor and the… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 2 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `H-01` — Centralized Control over Token Supply and Metadata  *(Severity: High · Status: Unresolved)*

The `mint` and `setMetadata` functions in the Memecoin contract are restricted to the `Flaunch` contract via the `onlyFlaunch` modifier. This grants the `Flaunch` contract, and by extension its owner, complete and centralized control over the token's total supply (through arbitrary minting) and its public metadata (name and symbol). A compromise of the `Flaunch` contract or a malicious action by its owner could lead to arbitrary token inflation or misleading token information, severely undermining the Memecoin's integrity and value.

**Recommendation:** Implement a more decentralized or time-locked approach for critical functions like minting and metadata changes. Consider introducing a multi-signature wallet or a governance mechanism (e.g., via ERC20Votes) for `Flaunch`'s owner to approve such actions. If full decentralization is not feasible, ensure the `Flaunch` contract itself is secured with robust access controls and audited thoroughly.


### `M-01` — Irreversible Infinite Allowance for Permit2  *(Severity: Medium · Status: Unresolved)*

The Memecoin contract implements special logic for the `_PERMIT2` address (0x00...8BA3). The `allowance` function is overridden to always return `type(uint).max` for `_PERMIT2`, and the `approve` function reverts if an approval for `_PERMIT2` is attempted with any amount other than `type(uint).max`. This design choice means that once a user interacts with Permit2 for this token, they effectively grant an irreversible infinite allowance to Permit2, which cannot be revoked or reduced. While this is a common pattern for Permit2 integration, it represents a significant security consideration for users who might not fully understand the implications of granting such an allowance.

**Recommendation:** Clearly communicate this irreversible infinite allowance behavior to users interacting with Permit2. Consider adding documentation or warnings within the dApp interface to ensure users are fully aware of the implications before approving Permit2. While a design choice, transparency is key to user security.


### `M-02` — High Dependency on External Flaunch Contract Security  *(Severity: Medium · Status: Unresolved)*

The Memecoin contract exhibits a high degree of dependency on the external `Flaunch` contract. Critical functionalities such as token minting permissions (`onlyFlaunch` modifier), retrieving the token's creator (`creator()`), and determining the treasury address (`treasury()`) all rely on calls to the `Flaunch` contract. The security and correct functioning of Memecoin are therefore directly tied to the security and integrity of the `Flaunch` contract. Any vulnerability, exploit, or malicious action within `Flaunch` could directly compromise the Memecoin contract and its ecosystem.

**Recommendation:** Conduct a comprehensive and independent security audit of the `Flaunch` contract to identify and mitigate any potential vulnerabilities. Ensure that `Flaunch` adheres to best security practices, including robust access control, reentrancy protection, and secure handling of external calls. Implement monitoring for `Flaunch` to detect any unusual activity.


### `L-01` — Potential for `flaunch` Address Misconfiguration During Upgrade  *(Severity: Low · Status: Unresolved)*

The `flaunch` address, which is critical for access control and functionality, is set during the `initialize` function. While OpenZeppelin's `initializer` modifier prevents re-initialization of the same function, there is a theoretical risk during future contract upgrades. If a new `initialize` function is introduced in an upgrade, or if a vulnerability allows bypassing the `initializer` modifier, the `flaunch` address could be reset to an arbitrary or malicious address. This could lead to an attacker gaining control over minting and metadata functions.

**Recommendation:** When performing upgrades, meticulously review all new code, especially any `initialize` functions or constructor logic, to ensure that the `flaunch` address cannot be inadvertently or maliciously reset. Adhere strictly to upgradeable contract best practices, including using `_gap` storage for future state variables to prevent storage collisions and thorough testing of upgrade paths.


### `I-01` — Incomplete Flaunch Contract Code Provided  *(Severity: Informational · Status: Unresolved)*

The provided source code for the `Flaunch` contract is truncated. As the `Memecoin` contract heavily relies on `Flaunch` for critical functionalities such as minting permissions, creator information, and treasury addresses, a full security assessment of `Memecoin`'s external dependencies, especially the `Flaunch` contract's logic, could not be completed. This limits the scope of the current audit regarding the overall ecosystem's security.

**Recommendation:** Provide the complete and verified source code for the `Flaunch` contract to enable a comprehensive security audit of the entire system. This is crucial for understanding the full risk profile of the Memecoin token.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x0086...d959`](https://basescan.org/address/0x0086cff0c1e5d17b19f5bcd4c8840a5b4251d959) |
| **Network** | Base |
| **Price** | $0.00000453 |
| **24h Volume** | $39.4K |
| **Liquidity** | $144.4K |
| **Volume / Liquidity** | 0.3× |
| **Token Age** | 7mo |
| **Top-10 Holders** | 37.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 78 buys / 56 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/base/0xbf0f716999378af289863d0c7eb961793993a641a0a943ccc6bb45cb5713b3fb)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/odei-ai-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-23*
