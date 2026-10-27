---
token: Uniswap
ticker: UNI
network: arbitrum
risk_score: 17
status: low
date: 2026-09-23
---

# Uniswap (UNI) — Smart Contract Security Analysis | Arbitrum

> **Risk Score: 17/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/uniswap-arb)

---

## Audit Summary

The audit of the StandardArbERC20 token implementation, deployed via a ClonableBeaconProxy, identified critical access control vulnerabilities related to its initialization process. Specifically, the `bridgeInit` function, which sets crucial operational parameters and the L2 gateway address, lacks proper access restrictions. This could allow an unauthorized entity to seize control of token minting and burning, or to disable core ERC20 metadata functions. Other findings include a potential limitation in string parsing and the inherent complexity of inline assembly, though these are of lower severity. The contract leverages OpenZeppelin standards and a modular architecture, but the identified critical flaws require immediate attention.

> **Final Recommendation:** Immediately implement robust access control for the `bridgeInit` function to ensure it can only be called once by a trusted entity. This is paramount to prevent unauthorized control over the token's minting/burning capabilities and to secure the ERC20 metadata functions. Review and clarify the string parsing logic in `BytesParser.toString` to ensure it handles all expected inputs gracefully or document its limitations. Conduct thorough testing of all initialization and upgrade paths to confirm secure operation and prevent front-running or re-initialization attacks.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 9/10 | Low | The contract exhibits a modular architecture (7.1) by inheriting from `L2GatewayToken` and `Cloneable`, and utilizes OpenZeppelin standards for ERC20 functionality, which generally contributes to… |
| **Governance / Economics** | 5/10 | Medium | The economic model (7.4) relies on the `l2Gateway` address for controlling `bridgeMint` and `bridgeBurn` functions, which is a standard and secure approach when properly managed. However, the… |
| **Upgrades** | 1/10 | High | The contract is designed as an implementation for a `ClonableBeaconProxy` (7.7), indicating a standard and flexible upgrade mechanism. This pattern allows for efficient upgrades across multiple proxy… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Beacon |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | 20.2% |
| **Top-3 Unlocked** | 39.0% |

## Security Findings

_🟡 3 Medium · 🟢 2 Low · ⚪ 1 Informational_

### `M-01` — Ambiguous or Restrictive String Parsing in BytesParser.toString  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `BytesParser.toString` library function has specific logic for handling 32-byte inputs. If `input.length == 32`, it explicitly checks if `input[31]` is `bytes1(0x00)`. If it's not null, the parsing fails (`return (false, res)`). This implies that 32-byte strings must be null-terminated to be successfully parsed by this branch. If an L1 token's name or symbol is exactly 32 bytes long and not null-terminated, it will fail to parse, potentially causing the `name()` or `symbol()` functions in `StandardArbERC20` to revert if `ignoreName` or `ignoreSymbol` is set to `true` (due to parsing failure during `bridgeInit`). Th

**Recommendation:** Clarify the intended encoding standard for 32-byte strings within the Arbitrum bridge documentation. If non-null-terminated 32-byte strings are expected, adjust the `BytesParser.toString` logic to handle them correctly, possibly by using `abi.decode(input, (string))` for all string lengths, or by providing a more robust parsing mechanism. Ensure that the parsing logic is resilient to various valid string encodings to prevent unexpected reverts.


### `M-02` — Unprotected Re-initialization of ERC20 Getters State  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `bridgeInit` function, which sets the `availableGetters` struct, is `public` and lacks any access control or an `initializer` modifier. While `L2GatewayToken._initialize` prevents re-initialization of `l2Gateway` and `l1Address`, the `availableGetters` state variable can be modified multiple times by any external caller. An attacker could call `bridgeInit` with malformed `_data` to intentionally cause `BytesParser.toString` or `BytesParser.toUint8` to fail, thereby setting `ignoreName`, `ignoreSymbol`, or `ignoreDecimals` to `true`. This would cause the `name()`, `symbol()`, or `decimals()` functions to revert for

**Recommendation:** Implement an `initializer` modifier (e.g., from OpenZeppelin's `Initializable` contract) on the `bridgeInit` function to ensure it can only be called once. Alternatively, add an `onlyOwner` or similar access control mechanism to restrict who can call this function and prevent unauthorized modification of `availableGetters`.


### `M-03` — Unprotected Initialization of L2 Gateway Address  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `bridgeInit` function is `public` and lacks any access control. This function calls `L2GatewayToken._initialize`, passing `msg.sender` as the `l2Gateway_` parameter. The `l2Gateway` address is critical as it controls the `bridgeMint` and `bridgeBurn` functions, which directly affect the token's supply. Since `bridgeInit` can be called by anyone, the first caller can front-run the legitimate initialization and set the `l2Gateway` to an arbitrary address they control. This grants the attacker full control over the token's minting and burning capabilities, leading to a complete loss of funds or unauthorized supply man

**Recommendation:** The `bridgeInit` function must be protected by an `initializer` modifier (e.g., from OpenZeppelin's `Initializable` contract) to ensure it can only be called once. Additionally, the `initializer` should be callable only by a trusted deployer or governance mechanism to securely set the `l2Gateway` address.


### `L-01` — Reliance on Low-Level Assembly in BytesLib  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `BytesLib` contract utilizes inline assembly (`mload`, `add`, `div`) for byte manipulation and type conversions (e.g., `toAddress`, `toUint8`, `toUint`). While the current implementation appears correct and includes bounds checks (`require(_bytes.length >= (_start + N))`), inline assembly is inherently more complex and error-prone than high-level Solidity. Any future modifications or incorrect usage could introduce subtle bugs that are difficult to detect and debug, potentially leading to incorrect data parsing or unexpected behavior.

**Recommendation:** Thoroughly document the assembly logic within `BytesLib` to explain its functionality and assumptions. Consider if `abi.decode` or other high-level Solidity constructs could achieve the same functionality with reduced complexity and improved readability, especially if performance is not a critical bottleneck. Ensure comprehensive unit tests cover all edge cases for these assembly functions.


### `L-02` — Presence of safeSelfDestruct in Cloneable Contract  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `Cloneable` base contract includes an `internal` function `safeSelfDestruct`. While it correctly prevents the master copy from being self-destructed via `require(!isMasterCopy, NOT_CLONE);`, the presence of a `selfdestruct` function, even if internal, introduces a powerful capability. If a derived contract were to expose this function externally, or if there was an unforeseen way to call it on a cloned instance, it could lead to the permanent disabling of a token instance. In the current `StandardArbERC20` contract, `safeSelfDestruct` is not called.

**Recommendation:** Ensure that `safeSelfDestruct` is never exposed externally in any derived contract. If this functionality is not intended to be used by the token instances, consider removing the function entirely from the `Cloneable` contract to eliminate any potential for misuse or accidental invocation.


### `I-01` — Design Choice for Conditional ERC20 Getters  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `StandardArbERC20` contract implements `decimals()`, `name()`, and `symbol()` functions that conditionally revert based on the `ignoreDecimals`, `ignoreName`, and `ignoreSymbol` flags within the `availableGetters` struct. These flags are set during `bridgeInit` based on the success of parsing the L1 token's metadata. This design allows the token to function even if some metadata is unavailable or malformed, but it means that basic ERC20 getter functions might revert, which could be unexpected for users or integrations expecting standard ERC20 behavior.

**Recommendation:** Document this design choice clearly for users and integrators, explaining that `decimals()`, `name()`, or `symbol()` might revert under certain conditions. Ensure that the `bridgeInit` function is always called with valid and complete metadata by a trusted entity to minimize the chances of these flags being set to `true` in production.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xfa7f...f7f0`](https://arbiscan.io/address/0xfa7f8980b0f1e64a2062791cc3b0871572f1f7f0) |
| **Network** | Arbitrum |
| **Price** | $10.2200 |
| **24h Volume** | $795.4K |
| **Liquidity** | $557.4K |
| **Volume / Liquidity** | 1.4× |
| **Token Age** | 1y |
| **Top-10 Holders** | 54.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1457 buys / 1685 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Sources

- [View on DexScreener](https://dexscreener.com/arbitrum/0xc24f7d8e51a64dc1238880bd00bb961d54cbeb29)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/uniswap-arb)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-23*
