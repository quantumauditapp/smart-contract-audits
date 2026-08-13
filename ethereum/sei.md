---
token: SEI
ticker: SEI
network: ethereum
risk_score: 62
status: high
date: 2026-08-13
---

# SEI (SEI) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 62/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/sei-eth)

---

## Audit Summary

This audit was conducted on a partial codebase consisting solely of interfaces and two utility libraries (`AddressCast`, `OFTComposeMsgCodec`). The core contract, `OFTImplementation`, which would contain the primary business logic, state management, and access control mechanisms, was not provided. Consequently, a comprehensive security assessment of the protocol's functionality, economic model, and governance structure is not possible. The identified risks primarily relate to the inherent limitations of reviewing an incomplete system and potential complexities within the provided libraries.

> **Final Recommendation:** A comprehensive security audit requires access to the complete and deployed source code of the `OFTImplementation` contract. Without this crucial component, any security assessment is inherently incomplete and cannot guarantee the safety of the protocol. It is strongly recommended to provide the full codebase for a thorough review covering all aspects of smart contract security, including reentrancy, access control, economic models, and upgradeability. Additionally, ensure that all critical administrative functions within the `OFTImplementation` are protected by robust, multi-signature based access control.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The provided codebase consists of well-defined interfaces and two utility libraries, `AddressCast` and `OFTComposeMsgCodec`. The `AddressCast` library includes robust input validation for address… |
| **Governance / Economics** | 2/10 | High | Due to the absence of the `OFTImplementation` contract, it is impossible to assess the protocol's governance model, economic stability, or potential for oracle manipulation (7.4 Economic, 7.5… |
| **Upgrades** | 6/10 | Medium | The provided information states `is_proxy: false`, suggesting the `OFTImplementation` might not be directly upgradeable via a proxy pattern. However, without the actual contract code, it's impossible… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 99.9% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🔴 1 Critical · 🟡 1 Medium · 🟢 1 Low · ⚪ 2 Informational_

### `C-01` — Incomplete Codebase for Audit (Missing OFTImplementation)  *(Severity: Critical · Status: Unresolved)*

The primary contract, `OFTImplementation`, which is expected to contain the core business logic, state variables, and access control mechanisms for the Omnichain Fungible Token, was not provided for review. This prevents a comprehensive security assessment of the protocol's functionality, potential vulnerabilities (e.g., reentrancy, integer overflows, access control flaws), and overall system integrity. Without the implementation, the actual security posture of the protocol cannot be determined.

**Recommendation:** Provide the complete and verified source code for the `OFTImplementation` contract to enable a full and accurate security audit. This is essential for identifying and mitigating potential vulnerabilities before deployment or further integration.


### `M-01` — Potential for Misinterpretation with `abi.encodePacked` in `OFTComposeMsgCodec`  *(Severity: Medium · Status: Unresolved)*

The `OFTComposeMsgCodec` library utilizes `abi.encodePacked` for message encoding. While this is a common practice for cross-chain messaging, `abi.encodePacked` does not add padding and can lead to ambiguity or misinterpretation if the decoding logic on the receiving chain or within other parts of the protocol does not precisely match the encoding structure, especially when dealing with variable-length data (`bytes _composeMsg`). A mismatch could lead to incorrect parsing of message components like `nonce`, `srcEid`, or `amountLD`.

**Recommendation:** Ensure that all decoding logic strictly adheres to the exact encoding structure defined in `OFTComposeMsgCodec`. Consider adding explicit length prefixes for variable-length data within the `_composeMsg` if not already handled by the underlying LayerZero messaging system, or use `abi.encode` for fixed-size encoding where possible to reduce ambiguity. Thorough cross-chain testing of message encoding and decoding is crucial.


### `L-01` — Low-Level Assembly in `AddressCast.toBytes`  *(Severity: Low · Status: Unresolved)*

The `AddressCast.toBytes` function employs inline assembly for byte manipulation. While the function includes size checks and appears to correctly handle the conversion, assembly code is inherently more complex and less readable than high-level Solidity. This increases the risk of subtle bugs, off-by-one errors, or unexpected behavior if not rigorously tested across all edge cases, potentially leading to incorrect address or byte array representations.

**Recommendation:** Thoroughly review and test the `AddressCast.toBytes` function with a wide range of inputs, including edge cases for `_size` (e.g., 1, 32) and `_addressBytes32` values. Consider adding comprehensive unit tests to ensure its correctness and resilience. If possible, explore alternative high-level Solidity constructs that achieve the same functionality to improve readability and reduce potential error surface.


### `I-01` — Extensive Interface Definitions Indicate High System Complexity  *(Severity: Informational · Status: Unresolved)*

The provided codebase includes a significant number of interfaces (`IMessageLibManager`, `IMessagingChannel`, `IMessagingComposer`, `IPreCrime`, etc.). While this modular design promotes separation of concerns and reusability, a large number of interconnected interfaces suggests a highly complex system architecture. Increased complexity can lead to a larger attack surface, make it more challenging to reason about the overall system's security, and increase the potential for integration errors between different components.

**Recommendation:** Maintain clear and comprehensive documentation for the entire system, detailing the responsibilities of each interface and how they interact. Implement robust integration testing to ensure seamless and secure communication between all components. Consider architectural reviews to identify and simplify any overly complex interdependencies.


### `I-02` — Lack of Access Control Context in Interfaces  *(Severity: Informational · Status: Unresolved)*

Several functions defined within the interfaces (e.g., `registerLibrary`, `setDefaultSendLibrary`, `setEnforcedOptions` in `IMessageLibManager`, `setEnforcedOptions` in `IOAppOptionsType3`) imply privileged administrative actions. Without the concrete implementation of these interfaces, it is impossible to verify if robust access control mechanisms (e.g., `onlyOwner`, role-based access control, multi-signature wallets) are properly applied to prevent unauthorized users from invoking these critical functions and altering protocol parameters.

**Recommendation:** Ensure that all functions within the `OFTImplementation` that correspond to these privileged interface methods are protected by strong access control. Implement a multi-signature wallet for critical administrative roles to enhance security and decentralization. Clearly document the access control policies for each sensitive function.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xbdf4...788b`](https://etherscan.io/address/0xbdf43ecadc5cef51b7d1772f722e40596bc1788b) |
| **Network** | Ethereum |
| **Price** | $0.04144 |
| **24h Volume** | $434.9K |
| **Liquidity** | $2.05M |
| **Volume / Liquidity** | 0.2× |
| **Token Age** | 1y |
| **Top-10 Holders** | 98.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 190 buys / 93 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0xf8e349d1d827a6edf17ee673664cfad4ca78c533)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/sei-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-13*
