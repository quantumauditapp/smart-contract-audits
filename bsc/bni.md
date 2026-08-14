---
token: BNI
ticker: BNI
network: bsc
risk_score: 4
status: low
date: 2026-08-14
---

# BNI (BNI) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 4/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/bni-bsc)

---

## Audit Summary

This audit covers the OpenZeppelin `Address.sol` library, a foundational component for secure address interactions in Solidity. The library itself is highly robust, well-tested, and adheres to best practices, providing essential utilities like safe value transfers and low-level call wrappers. While the library is secure, its functions require careful integration and understanding by consuming contracts to prevent common vulnerabilities such as reentrancy or incorrect handling of external calls. The audit identifies several informational points regarding the intended use and limitations of its functions.

> **Final Recommendation:** While the OpenZeppelin `Address.sol` library is inherently secure and well-audited, consuming contracts must exercise diligence in its integration. Developers should thoroughly review the NatSpec documentation for each function, paying particular attention to warnings regarding reentrancy, external call safety, and the limitations of `isContract`. Implement the Checks-Effects-Interactions pattern consistently when using functions that perform external calls, and consider using reentrancy guards where appropriate. Ensure that any contract interacting with `Address.sol` adheres to secure development best practices to mitigate risks arising from misuse.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The `Address.sol` library demonstrates high technical quality, adhering to secure coding standards and providing robust utilities for EVM interactions (7.2 Code Security). Functions like `sendValue`… |
| **Governance / Economics** | 7/10 | Low | As a foundational utility library, `Address.sol` does not implement any economic mechanisms (7.4 Economic) or governance structures (7.5 Governance). Therefore, there are no inherent economic or… |
| **Upgrades** | 10/10 | Low | The `Address.sol` contract is a library and is not designed to be upgradeable via proxy patterns (7.7 Upgrades). It is typically deployed as an immutable component or included directly in other… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Null Address |

## Security Findings

_🟢 1 Low · ⚪ 4 Informational_

### `L-01` — Reliance on Calling Contract for External Call Safety  *(Severity: Low · Status: Unresolved)*

The `Address.sol` library provides robust primitives for interacting with external addresses, including sending value and making arbitrary calls. However, the ultimate responsibility for ensuring the security of these interactions, such as preventing reentrancy or handling unexpected external contract behavior, lies with the contract that integrates and utilizes these library functions. A lack of proper implementation of the Checks-Effects-Interactions pattern or reentrancy guards in the calling contract can lead to vulnerabilities (7.2 Code Security, 7.6 External).

**Recommendation:** All contracts integrating `Address.sol` functions that perform external calls must implement the Checks-Effects-Interactions pattern. State changes should occur before any external calls. Additionally, consider using reentrancy guards for functions that transfer assets or modify critical state after an external call. Thoroughly test all external interactions.


### `I-01` — Limitations of `isContract` Function  *(Severity: Informational · Status: Unresolved)*

The `isContract` function, while correctly implemented, has inherent limitations as explicitly noted in its NatSpec documentation. It returns `false` for contracts in construction, externally-owned accounts (EOAs), addresses where a contract will be created, or where a contract was destroyed. It also returns `true` for contracts scheduled for `SELFDESTRUCT` within the same transaction. Relying on `isContract` alone for security, especially against flash loan attacks or to distinguish EOAs from contracts, is explicitly discouraged by OpenZeppelin (7.2 Code Security).

**Recommendation:** Developers should be fully aware of the limitations of `isContract` and avoid using it as a primary security mechanism, particularly for preventing calls from contracts or protecting against flash loan attacks. Implement robust access control mechanisms and reentrancy guards instead of relying on `isContract` for such purposes.


### `I-02` — `sendValue` Reentrancy Warning  *(Severity: Informational · Status: Unresolved)*

The `sendValue` function, which replaces Solidity's `transfer` for sending ETH, explicitly warns about the potential for reentrancy vulnerabilities due to control being transferred to the recipient. While `sendValue` itself is a safe way to send ETH by forwarding all available gas, the calling contract must implement proper reentrancy protection (e.g., `ReentrancyGuard` or the Checks-Effects-Interactions pattern) to prevent malicious re-entry attacks (7.2 Code Security).

**Recommendation:** When using `sendValue` or any function that performs external calls, ensure that the calling contract strictly adheres to the Checks-Effects-Interactions pattern. Integrate a reentrancy guard mechanism (e.g., OpenZeppelin's `ReentrancyGuard`) in functions that modify state before making external calls to untrusted addresses.


### `I-03` — Usage of Low-Level Call Functions  *(Severity: Informational · Status: Unresolved)*

The library provides several `functionCall` variants for performing low-level `call`, `staticcall`, and `delegatecall` operations. These functions are correctly implemented with error handling and revert bubbling. However, low-level calls inherently carry risks if the target contract is untrusted, malicious, or buggy. Misuse of these functions, especially `delegatecall`, can lead to critical vulnerabilities in the calling contract if not handled with extreme care (7.2 Code Security).

**Recommendation:** Developers should use low-level call functions only when absolutely necessary and with a thorough understanding of their implications. Always validate the target address and the `data` payload. For `delegatecall`, ensure the target contract is fully trusted and compatible with the calling contract's storage layout to prevent storage collisions or unexpected behavior.


### `I-04` — Library Nature and Integration Risk  *(Severity: Informational · Status: Unresolved)*

As a utility library, `Address.sol` is designed to be imported and used by other contracts. While the library itself is highly secure and well-audited, its security posture within a larger system is dependent on the correct and secure integration by consuming contracts. Flaws in the application logic of contracts using `Address.sol` could inadvertently introduce vulnerabilities, even if the library functions are used as intended (7.1 Architecture, 7.6 External).

**Recommendation:** Developers should treat the integration of `Address.sol` (and any external library) as a critical security boundary. Comprehensive unit and integration testing should be performed on all functions that utilize `Address.sol` utilities. A holistic security review of the entire system, including how `Address.sol` is used, is recommended.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x209e...ffff`](https://bscscan.com/address/0x209e1c94a88318e2eae570bce87936589a90ffff) |
| **Network** | BNB Chain |
| **Price** | $0.0001381 |
| **24h Volume** | $186.5K |
| **Liquidity** | $35.2K |
| **Volume / Liquidity** | 5.3× |
| **Token Age** | 1mo |
| **Top-10 Holders** | 144.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 942 buys / 714 sells |

## Security Flags (5/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x04daaa7088ee209101f33198f2da86c05b539121)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/bni-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-14*
