---
token: ArcBlock
ticker: ABT
network: ethereum
risk_score: 91
status: critical
date: 2026-09-28
---

# ArcBlock (ABT) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 91/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/arcblock-eth)

---

## Audit Summary

The ArcBlock Token contract is a standard ERC-20 implementation with pausable functionality and centralized ownership. While it correctly utilizes SafeMath for arithmetic operations and includes mitigations for the ERC-20 approve race condition, significant risks stem from the use of an outdated Solidity compiler version and the reliance on a single EOA for critical administrative control. The pausable mechanism, while intended for emergencies, also introduces a centralized point of control over token operations.

> **Final Recommendation:** It is strongly recommended to migrate the contract ownership to a robust multi-signature wallet to eliminate the single point of failure associated with the current EOA owner. For any future token deployments or major protocol iterations, consider utilizing a modern Solidity compiler version (0.8.x) to leverage the latest security features and optimizations. Additionally, educate users on the safer `increaseApproval` and `decreaseApproval` functions to mitigate the ERC-20 `approve` race condition. Review the necessity and implementation of the pausable mechanism, potentially introducing a time-lock or multi-sig requirement for its activation to enhance decentralization and reduce operational risk.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 4/10 | Medium | The contract implements the ERC-20 standard correctly, utilizing the SafeMath library to prevent integer overflows/underflows (7.2 Code Security). It also provides `increaseApproval` and… |
| **Governance / Economics** | 1/10 | High | The contract employs a centralized `Ownable` pattern, granting a single EOA full control over critical functions like pausing token transfers and ownership transfer (7.3 Access Control, 7.5… |
| **Upgrades** | 4/10 | Medium | The ArcBlock Token contract is a standard, non-upgradeable implementation. It does not utilize any proxy patterns (e.g., UUPS, Transparent) or other mechanisms for on-chain upgradeability (7.7… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 92.2% |
| **Top-3 Unlocked** | ⚠️ 97.0% |

## Security Findings

_🟠 2 High · 🟡 3 Medium · 🟢 1 Low_

### `H-01` — Centralized Control and Single Point of Failure (Owner EOA)  *(Severity: High · Status: Unresolved)*

The contract relies on a single EOA (`0x4fd95f61a1b52b3c272ae449e95cfc307d19afd6`) for critical administrative functions such as pausing transfers and transferring ownership. This creates a single point of failure, as compromise of this EOA's private key could lead to malicious control or loss of administrative capabilities (7.3 Access Control, 7.8 Operations).

**Recommendation:** Consider migrating ownership to a multi-signature wallet (e.g., Gnosis Safe) to distribute control and enhance security against single points of failure.


### `H-02` — Outdated Solidity Compiler Version  *(Severity: High · Status: Unresolved)*

The contract is compiled with `pragma solidity ^0.4.13`, which is a significantly outdated Solidity version. Older compiler versions may contain known or undiscovered bugs, lack modern security features (e.g., custom error messages with `require`), and result in less optimized bytecode (7.2 Code Security).

**Recommendation:** For new deployments or major upgrades, consider migrating to a more recent and actively supported Solidity compiler version (e.g., 0.8.x) to benefit from security improvements, bug fixes, and enhanced language features.


### `M-01` — Pausable Mechanism Centralization Risk  *(Severity: Medium · Status: Unresolved)*

The `Pausable` mechanism allows the contract owner to unilaterally halt all token transfers and approvals. While intended for emergency situations, this centralized control can lead to a denial of service for token holders, impacting liquidity and utility, if misused or if the owner's key is compromised (7.3 Access Control, 7.4 Economic).

**Recommendation:** Clearly communicate the purpose and conditions under which the pause function would be invoked. Consider implementing a time-locked pause or a multi-signature approval for pausing to decentralize this critical control.


### `M-02` — ERC-20 `approve` Race Condition Vulnerability  *(Severity: Medium · Status: Unresolved)*

The `approve` function is susceptible to a known ERC-20 race condition. If a user approves an amount and then attempts to change that approval to a different amount, a malicious spender could front-run the second transaction, spending the original approved amount before the new approval takes effect, and then spending the new approved amount. While `increaseApproval` and `decreaseApproval` functions are provided to mitigate this, the base `approve` function remains vulnerable (7.2 Code Security).

**Recommendation:** Advise users to exclusively use `increaseApproval` and `decreaseApproval` when adjusting allowances, rather than directly calling `approve` with a new value, to prevent potential front-running exploits.


### `M-03` — SafeMath `assert` Usage for Revert Conditions  *(Severity: Medium · Status: Unresolved)*

The `SafeMath` library used in the contract employs `assert` statements for overflow/underflow checks. In Solidity, `assert` consumes all remaining gas when it fails, whereas `require` refunds unused gas. While functionally correct for these checks, using `assert` is less gas-efficient than `require` for conditions that should revert due to invalid input or state (7.2 Code Security).

**Recommendation:** For future contracts or major refactors, consider updating the `SafeMath` library to use `require` statements instead of `assert` for conditions that are expected to be met by valid input, improving gas efficiency on reverts.


### `L-01` — Missing Division by Zero Check in SafeMath.div  *(Severity: Low · Status: Unresolved)*

The `SafeMath.div` function does not explicitly check for division by zero. While this specific function is not directly utilized in the `ArcBlockToken` contract's core logic, its presence in the library could pose a risk if other parts of the system were to use it or if the contract were extended (7.2 Code Security).

**Recommendation:** Add a `require(b > 0, "division by zero")` check at the beginning of the `SafeMath.div` function to prevent potential runtime errors if it were to be used.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xb98d...e986`](https://etherscan.io/address/0xb98d4c97425d9908e66e53a6fdf673acca0be986) |
| **Network** | Ethereum |
| **Price** | $0.3616 |
| **24h Volume** | $133.0K |
| **Liquidity** | $192.0K |
| **Volume / Liquidity** | 0.7× |
| **Token Age** | 2y |
| **Top-10 Holders** | 71.3% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 198 buys / 190 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0x677d05b8bc5c691afd0dcb8ed81404c1ebe114d6)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/arcblock-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-28*
