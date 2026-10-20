---
token: Lido DAO Token
ticker: LDO
network: arbitrum
risk_score: 23
status: low
date: 2026-09-25
---

# Lido DAO Token (LDO) — Smart Contract Security Analysis | Arbitrum

> **Risk Score: 23/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/lido-dao-token-arb)

---

## Audit Summary

The audit of the StandardArbERC20 implementation contract, used via a ClonableBeaconProxy, revealed a Medium risk issue related to ambiguous string parsing logic in the `BytesParser` library, which could lead to incorrect token metadata. A Low risk issue was identified regarding ERC20 getters that can revert, potentially causing compatibility problems. The contract demonstrates robust access control for critical functions and a secure upgrade pattern.

> **Final Recommendation:** Review and refactor the `BytesParser.toString` function to ensure consistent and unambiguous handling of string inputs, especially regarding length and encoding assumptions, to prevent misinterpretation of token metadata. Consider modifying the `name()`, `symbol()`, and `decimals()` functions to return default or empty values instead of reverting, or provide clear documentation for integrators regarding this non-standard ERC20 behavior. Ensure all external systems interacting with this token are aware of the potential for these getters to revert.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 9/10 | Low | The contract's architecture (7.1) is well-structured, utilizing OpenZeppelin upgradeable patterns and a `Cloneable` base for beacon proxy compatibility. Code security (7.2) is generally good, with… |
| **Governance / Economics** | 3/10 | High | The contract functions as an L2 ERC20 token, with its economic model (7.4) being a standard fungible token. Minting and burning are controlled by a designated `l2Gateway` address, ensuring… |
| **Upgrades** | 1/10 | High | The contract is designed as an implementation for a `ClonableBeaconProxy`, indicating a robust upgradeability pattern (7.7). The `Cloneable` base contract correctly distinguishes between the master… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Beacon |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## Security Findings

_🟡 1 Medium · 🟢 1 Low · ⚪ 2 Informational_

### `M-01` — Ambiguous and Inconsistent String Parsing in `BytesParser.toString`  *(Severity: Medium · Status: Unresolved)*

The `BytesParser.toString` function exhibits complex and inconsistent logic for parsing byte arrays into strings. Specifically, it has three distinct branches based on `input.length`: 1) `input.length == 0` returns `(false, "")`. 2) `input.length == 32` checks for null-termination at `input[31]` and then truncates trailing null bytes. If `input[31]` is not `0x00`, it returns `(false, "")`. This implies a specific, non-standard encoding for 32-byte strings. 3) `else` (any other length) directly uses `abi.decode(input, (string))`. This is problematic because `abi.decode` expects ABI-encoded data, which includes a length prefix for dynamic types like `string`. If `input` contains raw bytes (e.…

**Recommendation:** Refactor `BytesParser.toString` to use a single, clear, and standard method for decoding strings from bytes. If raw bytes are expected, implement a robust decoding logic that handles length and padding explicitly, rather than relying on `abi.decode` for non-ABI-encoded data. Ensure consistency across all possible input lengths and document the expected byte encoding format.


### `L-01` — ERC20 Getters Can Revert  *(Severity: Low · Status: Unresolved)*

The `name()`, `symbol()`, and `decimals()` functions in `StandardArbERC20` are designed to revert if the corresponding `ignoreName`, `ignoreSymbol`, or `ignoreDecimals` flags are set during `bridgeInit`. This behavior deviates from the standard ERC20 interface, where these functions are expected to always return a value (even an empty string or zero for decimals if not applicable). Integrations such as wallets, block explorers, or other DeFi protocols often assume these getters will not revert, and their unexpected failure could lead to broken displays, failed transactions, or compatibility issues.

**Recommendation:** Consider modifying these getter functions to return default or empty values (e.g., `""` for name/symbol, `0` for decimals) instead of reverting when the `ignore` flag is set. Alternatively, provide comprehensive documentation for all external integrators, clearly outlining this non-standard behavior and its implications.


### `I-01` — Partial Re-initialization Possible for `availableGetters`  *(Severity: Informational · Status: Unresolved)*

The `bridgeInit` function, which serves as the initializer for the proxy, includes a check `require(l2Gateway == address(0), "ALREADY_INIT");` within `L2GatewayToken._initialize` to prevent re-initialization of `l2Gateway` and `l1Address`. However, the `availableGetters` struct in `StandardArbERC20` is set directly within `bridgeInit` *after* this check and is not protected by a similar one-time initialization guard. This means `availableGetters` can be modified if `bridgeInit` is called again by the `l2Gateway` (which is the `msg.sender` during initialization). While this only affects the behavior of the ERC20 getters (name, symbol, decimals) and is not a critical vulnerability, it represe…

**Recommendation:** Implement a boolean flag (e.g., `_initialized`) in `StandardArbERC20` to ensure that the `availableGetters` struct can only be set once during the initial `bridgeInit` call.


### `I-02` — Use of `extcodesize` for `isContract` Check  *(Severity: Informational · Status: Unresolved)*

The `isContract` function in `TransferAndCallToken` uses `extcodesize` to determine if an address belongs to a contract. While a common pattern, `extcodesize` returns zero during a contract's constructor execution, meaning a contract currently being deployed would be incorrectly identified as an EOA. Additionally, it can be manipulated in certain reentrancy scenarios where a contract calls itself during construction. In the context of `transferAndCall`, this check is performed on the `_to` address *after* the token transfer, mitigating most immediate risks.

**Recommendation:** Be aware of the limitations of `extcodesize`. For the current use case in `transferAndCall`, the risk is low. If more robust contract detection is needed in other contexts, consider alternative methods or ensure the timing of the check avoids constructor-related issues.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x13ad...fa60`](https://arbiscan.io/address/0x13ad51ed4f1b7e9dc168d8a00cb3f4ddd85efa60) |
| **Network** | Arbitrum |
| **Price** | $0.4472 |
| **24h Volume** | $34.2K |
| **Liquidity** | $71.9K |
| **Volume / Liquidity** | 0.5× |
| **Token Age** | 3y |
| **Top-10 Holders** | 23.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 188 buys / 168 sells |

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

- [View on DexScreener](https://dexscreener.com/arbitrum/0x52f9d14bed8ce6536da063aaf274ae2747ef4853)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/lido-dao-token-arb)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-25*
