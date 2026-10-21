---
token: Boop
ticker: BOOP
network: arbitrum
risk_score: 44
status: medium
date: 2026-09-01
---

# Boop (BOOP) — Smart Contract Security Analysis | Arbitrum

> **Risk Score: 44/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/boop-arb)

---

## Audit Summary

The Boop token contract implements standard ERC-20 functionality alongside custom features for anti-bot measures, transfer limits, and liquidity management. A significant limitation of this audit is that the provided source code for the critical `_transfer` function is truncated, preventing a complete assessment of its internal logic, fee mechanisms, and interaction with external components. This truncation introduces substantial uncertainty regarding the contract's full security posture.

> **Final Recommendation:** Address the critical issue of the truncated source code to enable a comprehensive security review, particularly for the `_transfer` function and any associated fee logic. Evaluate the extent of centralized control, considering implementing multi-signature wallets for critical owner functions or introducing time-locks for sensitive parameter changes to mitigate single points of failure. Ensure all critical state changes are accompanied by explicit event emissions for transparency and off-chain monitoring.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract utilizes Solidity 0.8.21 and `SafeMath` for arithmetic, although the latter is redundant due to native overflow checks. It incorporates anti-reentrancy measures with `lockTheSwap` for… |
| **Governance / Economics** | 4/10 | Medium | The `Boop` token's economic model includes a fixed total supply, marketing allocation, and mechanisms like `_maxTxAmount` and `_maxWalletSize` to manage token distribution and prevent large… |
| **Upgrades** | 8/10 | Low | The `Boop` contract is implemented as a standard, non-upgradeable token contract. This design choice ensures immutability, meaning the contract's logic cannot be altered post-deployment (7.7… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 93.9% |
| **Top-3 Unlocked** | ⚠️ 99.9% |

## Security Findings

_🔴 1 Critical · 🟠 2 High · 🟡 2 Medium · 🟢 1 Low_

### `C-01` — Truncated Code Prevents Full Audit  *(Severity: Critical · Status: Unresolved)*

The provided source code for the `_transfer` function is incomplete. The function, which is central to all token movements and likely contains critical logic for fees, anti-bot measures, and external interactions, is truncated at `_holderLastTransferTimestamp[tx.orig...`. This prevents a comprehensive security assessment of the contract's core functionality, leaving significant attack vectors and vulnerabilities potentially undiscovered (7.2 Code Security, 7.6 External).

**Recommendation:** Provide the complete and untruncated source code for all contract functions, especially the `_transfer` function, to allow for a thorough security audit.


### `H-01` — Centralized Control and Owner Privileges  *(Severity: High · Status: Unresolved)*

The contract owner, utilizing the `Ownable` pattern, possesses extensive control over critical contract parameters and operations. This includes the ability to manage `_maxTxAmount`, `_maxWalletSize`, `transferDelayEnabled`, `bots` mapping, and `tradingOpen` (though specific setter functions are not fully visible in the truncated code, their existence is implied by the state variables). This high degree of centralization introduces a single point of failure and potential for malicious activity or operational errors, such as pausing trading or blocking legitimate users (7.3 Access Control, 7.5 Governance, 7.8 Operations).

**Recommendation:** Consider decentralizing control where feasible, perhaps by implementing a multi-signature wallet for ownership or introducing time-locks for sensitive parameter changes. Clearly document all owner-controlled functions and their potential impact. Implement robust access control checks for all administrative functions.


### `H-02` — Constructor Ownership Transfer Logic  *(Severity: High · Status: Unresolved)*

The constructor includes logic `if (_lockOwner != msg.sender) transferOwnership(_lockOwner);` to transfer ownership. If `_lockOwner` is an incorrect address, a contract that cannot accept ownership, or `address(0)` (which would revert), the contract's ownership could become stuck or transferred to an unintended entity. This could lead to a loss of administrative control over critical contract functions (7.3 Access Control, 7.8 Operations).

**Recommendation:** Ensure that the `_lockOwner` address provided during deployment is correct, is an EOA or a contract capable of accepting ownership, and is the intended administrative address. Consider adding a two-step ownership transfer process for the constructor, where the `_lockOwner` must explicitly claim ownership.


### `M-01` — Redundant SafeMath Usage  *(Severity: Medium · Status: Unresolved)*

The contract uses the `SafeMath` library for arithmetic operations. While `SafeMath` is crucial for preventing integer overflows/underflows in Solidity versions prior to 0.8.0, Solidity 0.8.x and later versions include native overflow and underflow checks by default. Therefore, the explicit use of `SafeMath` adds unnecessary code complexity and slightly increases gas costs without providing additional security benefits in this compiler version (7.2 Code Security).

**Recommendation:** Remove the `SafeMath` library and its `using` directives. Rely on Solidity's native overflow/underflow checks for arithmetic operations, which are enabled by default in `pragma solidity 0.8.21`.


### `M-02` — Anti-Bot/Anti-Whale Mechanisms as DoS Vectors  *(Severity: Medium · Status: Unresolved)*

The contract implements several anti-bot and anti-whale mechanisms, including `_maxTxAmount`, `_maxWalletSize`, `transferDelayEnabled`, and the `bots` mapping. While intended to prevent malicious activity, these features grant significant power to the owner and can be misused or inadvertently cause denial of service for legitimate users, especially large holders, liquidity providers, or automated systems. For example, setting `_maxTxAmount` too low could prevent necessary liquidity movements (7.4 Economic, 7.8 Operations).

**Recommendation:** Carefully review the parameters and conditions for these anti-bot/anti-whale features. Ensure that they are configured to minimize impact on legitimate users and liquidity. Consider implementing a mechanism for users to appeal bot status or for the community to vote on parameter changes if decentralization is a goal.


### `L-01` — Lack of Event Emission for Critical State Changes  *(Severity: Low · Status: Unresolved)*

The provided code snippet does not show event emissions for changes to several critical contract parameters, such as `_maxWalletSize`, `transferDelayEnabled`, or updates to the `bots` mapping. While `MaxTxAmountUpdated` is present, comprehensive event logging for all configurable parameters is crucial for transparency, allowing off-chain applications and users to monitor changes and react accordingly (7.8 Operations).

**Recommendation:** Emit events whenever critical state variables or configuration parameters are modified. This enhances transparency and allows for better off-chain monitoring and auditing of contract behavior.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x13a7...72b3`](https://arbiscan.io/address/0x13a7dedb7169a17be92b0e3c7c2315b46f4772b3) |
| **Network** | Arbitrum |
| **Price** | $0.00001159 |
| **24h Volume** | $13.7K |
| **Liquidity** | $151.0K |
| **Volume / Liquidity** | 0.1× |
| **Token Age** | 2y |
| **Top-10 Holders** | 22.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 170 buys / 219 sells |

## Security Flags (4/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/arbitrum/0x184fb097196a4e2be8dfd44b341cb7d13b41ea7e)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/boop-arb)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-01*
