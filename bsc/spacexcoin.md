---
token: SpaceXcoin
ticker: SPACEXCOIN
network: bsc
risk_score: 34
status: medium
date: 2026-08-13
---

# SpaceXcoin (SPACEXCOIN) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 34/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/spacexcoin-bsc)

---

## Audit Summary

The `Address.sol` library from OpenZeppelin provides essential utilities for interacting with addresses and performing low-level calls. It is a well-audited and widely used component in the EVM ecosystem. While the library itself is robust and secure, its functions, particularly those involving external calls, require careful implementation by calling contracts to prevent common vulnerabilities like reentrancy and misuse of powerful primitives.

> **Final Recommendation:** Projects integrating the `Address.sol` library must prioritize secure usage patterns, especially when performing external calls. Always apply the Checks-Effects-Interactions pattern or use reentrancy guards when interacting with untrusted external contracts via `sendValue` or `functionCallWithValue`. Exercise extreme caution and thorough testing when utilizing `functionDelegateCall` to prevent storage collisions or unintended logic execution, particularly in upgradeable proxy environments. Ensure that any contract relying on `isContract` understands its inherent limitations.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 9/10 | Low | The `Address.sol` library provides robust and well-tested utilities for safe external interactions, including `sendValue` and various `functionCall` wrappers, which correctly handle success checks… |
| **Governance / Economics** | 5/10 | Medium | As a foundational utility library, `Address.sol` does not incorporate specific governance or economic mechanisms (7.4 Economic, 7.5 Governance). Its design is purely functional, providing low-level… |
| **Upgrades** | 9/10 | Low | The `Address.sol` library is typically integrated directly into contracts or linked, rather than being deployed as an upgradeable component (7.7 Upgrades). It does not implement proxy patterns or… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `H-01` — Reentrancy Risk from External Calls  *(Severity: High · Status: Unresolved)*

The `sendValue` and `functionCallWithValue` functions facilitate external calls, which are known vectors for reentrancy attacks. While the `Address` library itself is secure, calling contracts must implement the Checks-Effects-Interactions pattern or use reentrancy guards to prevent malicious re-entrances when interacting with untrusted external contracts. The library's documentation explicitly warns about this.

**Recommendation:** Calling contracts must ensure that state changes are completed before any external calls are made. Implement the Checks-Effects-Interactions pattern consistently or integrate a reentrancy guard mechanism (e.g., OpenZeppelin's `ReentrancyGuard`) in functions that perform external calls.


### `M-01` — Potential Misuse of `delegatecall`  *(Severity: Medium · Status: Unresolved)*

The `functionDelegateCall` function provides a low-level `delegatecall` wrapper. While correctly implemented within the library, `delegatecall` is a powerful and dangerous primitive. Incorrect usage in calling contracts, particularly in proxy patterns, can lead to storage collisions, unexpected behavior, or even critical vulnerabilities like arbitrary code execution or storage corruption if the target contract is not carefully managed.

**Recommendation:** Calling contracts should use `delegatecall` only when absolutely necessary and with extreme caution. Ensure that the target contract's storage layout is compatible with the calling contract's, and that the target contract's logic is fully trusted and audited. Thorough testing is crucial for any `delegatecall` implementation.


### `L-01` — Reliance on Caller's Security Practices  *(Severity: Low · Status: Unresolved)*

As a utility library, `Address.sol` provides low-level functionalities like sending value and making calls without enforcing specific access control or security patterns. The overall security of a system using this library heavily depends on the calling contracts correctly implementing security best practices, such as access control (7.3 Access Control), reentrancy prevention, and proper error handling (7.8 Operations).

**Recommendation:** Developers integrating this library must ensure that all functions utilizing `Address.sol`'s utilities are protected by appropriate access control mechanisms and adhere to robust security patterns to prevent unauthorized or malicious use.


### `I-01` — Limitations of `isContract` Function  *(Severity: Informational · Status: Unresolved)*

The `isContract` function, while useful for certain checks, has documented limitations. It may return `false` for contracts under construction, destroyed contracts, or addresses where a contract will be created. Furthermore, the library explicitly states that `isContract` should not be relied upon to protect against flash loan attacks or to prevent calls from contracts, as it can be circumvented.

**Recommendation:** Developers should be fully aware of the caveats associated with `isContract` and avoid using it for critical security checks where its limitations could be exploited. Consider alternative, more robust mechanisms for contract type verification or access control if strict differentiation is required.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xf225...ffff`](https://bscscan.com/address/0xf225e70162837a811c77dc2bb413a5c06e97ffff) |
| **Network** | BNB Chain |
| **Price** | $0.0005654 |
| **24h Volume** | $488.0K |
| **Liquidity** | $94.8K |
| **Volume / Liquidity** | 5.1× |
| **Token Age** | 3d |
| **Top-10 Holders** | 39.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2518 buys / 1971 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x9955ea00dd43747c9b5a49838a300291ad96a837)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/spacexcoin-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-13*
