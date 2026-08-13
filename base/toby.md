---
token: toby
ticker: TOBY
network: base
risk_score: 30
status: medium
date: 2026-08-13
---

# toby (TOBY) — Smart Contract Security Analysis | Base

> **Risk Score: 30/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/toby-base)

---

## Audit Summary

The toby token contract is a custom ERC20 implementation with owner-controlled functionalities. A critical vulnerability was identified in the access control mechanism, utilizing `tx.origin` instead of `msg.sender`, which exposes owner-restricted functions to phishing attacks. Additionally, the `transferFrom` function exhibits incorrect logic, and an unused state variable was found. The contract includes a token recovery mechanism for ERC20 tokens.

> **Final Recommendation:** It is critical to address the `tx.origin` vulnerability by replacing it with `msg.sender` in the `onlyOwner` modifier to prevent phishing attacks and unauthorized access to owner-controlled functions. The `transferFrom` function's logic should be corrected to ensure the allowance check precedes the token transfer, aligning with ERC20 standards and preventing gas waste. Consider using battle-tested OpenZeppelin contracts for ERC20 and Ownable implementations to leverage audited and secure code, reducing the risk of subtle bugs inherent in custom implementations.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 7/10 | Low | The contract implements a custom ERC20 token with standard functionalities like transfer, approve, mint, and burn (7.2 Code Security). It includes a useful `TokenRecover` mechanism allowing the owner… |
| **Governance / Economics** | 4/10 | Medium | The contract represents a simple ERC20 token with no complex economic models or governance mechanisms (7.4 Economic, 7.5 Governance). The initial supply is minted to a specified token owner during… |
| **Upgrades** | 6/10 | Medium | The contract is not designed to be upgradeable (7.7 Upgrades). It does not implement any proxy patterns, meaning its logic is immutable once deployed. This simplifies the architecture but requires… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 99.4% (≈ permanent lock) |
| **LP Locked** | 99.4% |

## Security Findings

_🔴 1 Critical · 🟠 1 High · 🟢 1 Low · ⚪ 1 Informational_

### `C-01` — `tx.origin` for Access Control  *(Severity: Critical · Status: Unresolved)*

The `onlyOwner` modifier in the `Ownable` contract uses `tx.origin` instead of `msg.sender` for access control. This is a critical vulnerability as it makes all owner-restricted functions susceptible to phishing attacks. If the legitimate owner interacts with a malicious contract, that contract can then call owner-restricted functions (e.g., `transferOwnership`, `renounceOwnership`, `recoverERC20`) on the `toby` token contract, as `tx.origin` would still resolve to the legitimate owner's address.

**Recommendation:** Replace `tx.origin` with `msg.sender` in the `onlyOwner` modifier. The `msg.sender` variable always refers to the immediate caller of the function, providing a secure and standard way to implement access control.


### `H-01` — Incorrect `transferFrom` Logic  *(Severity: High · Status: Unresolved)*

The `transferFrom` function executes the token transfer (`_transfer`) before checking if the allowance is sufficient and updating it. Specifically, `_transfer(sender, recipient, amount)` is called first, followed by `require(currentAllowance >= amount, "ERC20: transfer amount exceeds allowance")`. If the allowance is insufficient, the `_transfer` operation will still occur (if the sender has enough balance), but the transaction will then revert due to the subsequent `require` statement. This leads to wasted gas and non-standard ERC20 behavior, potentially causing issues for integrations expecting the allowance check to precede the transfer.

**Recommendation:** Reorder the operations within `transferFrom`. The allowance check (`require(currentAllowance >= amount)`) should occur before `_transfer(sender, recipient, amount)`. The correct sequence is: check allowance, perform transfer, then update allowance.


### `L-01` — Unused State Variable `Optimization`  *(Severity: Low · Status: Unresolved)*

The public state variable `Optimization` is declared and initialized with a large `uint256` value but is never read or used within any of the contract's functions. This adds unnecessary storage cost to the contract and can be misleading to developers or auditors regarding its purpose.

**Recommendation:** Remove the `Optimization` variable if it serves no functional purpose. If it is intended for future use, consider adding comments to explain its role or making it internal if it's not meant for external interaction.


### `I-01` — Custom ERC20 Implementation  *(Severity: Informational · Status: Unresolved)*

The contract utilizes a custom implementation of the ERC20 standard rather than leveraging battle-tested and widely audited libraries such as OpenZeppelin Contracts. While the current implementation largely adheres to the standard, custom code carries a higher inherent risk of introducing subtle bugs, edge cases, or non-compliance issues that might have been addressed in more mature libraries.

**Recommendation:** Consider migrating to OpenZeppelin's ERC20 implementation for enhanced security, reliability, and maintainability. If a custom implementation is deemed necessary, ensure comprehensive unit testing, formal verification, and thorough security audits are conducted to mitigate potential risks.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xb8d9...e56e`](https://basescan.org/address/0xb8d98a102b0079b69ffbc760c8d857a31653e56e) |
| **Network** | Base |
| **Price** | $0.00000001 |
| **24h Volume** | $49.2K |
| **Liquidity** | $177.1K |
| **Volume / Liquidity** | 0.3× |
| **Token Age** | 2y |
| **Top-10 Holders** | 22.5% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 465 buys / 713 sells |

## Security Flags (4/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/base/0xfe83058f06869da5d70a1355dca64c873480ab1d)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/toby-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-13*
