---
token: Spell Token
ticker: SPELL
network: arbitrum
risk_score: 26
status: low
date: 2026-09-27
---

# Spell Token (SPELL) — Smart Contract Security Analysis | Arbitrum

> **Risk Score: 26/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/spell-token-arb)

---

## Audit Summary

This audit covers the `StandardArbERC20` implementation contract, deployed via a `ClonableBeaconProxy` on Arbitrum. The contract functions as an L2 ERC20 token within the Arbitrum token bridge. Key findings include a critical re-initialization vulnerability in `bridgeInit` and a high-severity design flaw in the application of the `Cloneable` pattern within a proxy context. Several other issues of medium, low, and informational severity were identified, primarily related to initialization, metadata handling, and library usage.

> **Final Recommendation:** Prioritize addressing the critical re-initialization vulnerability in `bridgeInit` by implementing a robust initializer pattern. Re-evaluate the `Cloneable` base contract's role and implementation within the beacon proxy architecture to ensure `isMasterCopy` behaves as intended or remove it if unnecessary. Implement `_disableInitializers()` in the implementation's constructor to prevent storage collisions. Additionally, simplify and thoroughly test the `BytesParser.toString` function to mitigate potential metadata parsing issues.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The technical architecture (7.1) leverages OpenZeppelin's upgradeable patterns and custom libraries for L2 token bridging. Code security (7.2) benefits from standard ERC20 practices, but custom logic… |
| **Governance / Economics** | 2/10 | High | This contract serves as an L2 token implementation, with its economic model (7.4) inherently tied to its L1 counterpart and the L2 Gateway. The `onlyGateway` modifier effectively restricts critical… |
| **Upgrades** | 6/10 | Medium | The contract is designed for upgradeability using a ClonableBeaconProxy pattern (7.1, 7.7), allowing for efficient updates across multiple proxy instances. However, the `Cloneable` base contract's… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 72.8% |
| **Top-3 Unlocked** | ⚠️ 96.9% |

## Security Findings

_🟡 3 Medium · 🟢 2 Low · ⚪ 1 Informational_

### `M-01` — Medium: Denial of Service for ERC20 Metadata via Malformed `_data`  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `bridgeInit` function parses `_data` to set the token's name, symbol, and decimals. If `BytesParser.toString` or `BytesParser.toUint8` fails to parse the input (e.g., due to incorrect length or format), the corresponding `ignoreName`, `ignoreSymbol`, or `ignoreDecimals` flag is set to `true`. When these flags are `true`, the respective ERC20 metadata functions (`name()`, `symbol()`, `decimals()`) will revert. If `bridgeInit` is called with malformed data, either initially or maliciously (if C-01 is not resolved), it can lead to a permanent denial of service for these fundamental ERC20 functions (7.2 Code Security).

**Recommendation:** Beyond resolving C-01 to prevent re-initialization, consider stricter validation of the `_data` within `bridgeInit`. Instead of setting `ignore` flags, `bridgeInit` should revert if parsing of essential metadata fails. This ensures that the token is only initialized with valid and functional metadata.


### `M-02` — Critical: `bridgeInit` Lacks Proper Initialization Guard  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `bridgeInit` function in `StandardArbERC20` is `public virtual` and does not implement an `initializer` modifier or a similar 'only once' protection. While the internal `_initialize` function (called by `bridgeInit`) prevents `l2Gateway` from being set multiple times, `bridgeInit` itself can be called repeatedly. Subsequent calls would overwrite the `availableGetters` struct, potentially allowing an attacker to intentionally provide malformed `_data` to set `ignoreName`, `ignoreSymbol`, or `ignoreDecimals` to `true`. This would cause the `name()`, `symbol()`, or `decimals()` functions to revert for all users, leadi

**Recommendation:** Implement a robust 'only once' initialization guard for `bridgeInit`. This can be achieved by inheriting from OpenZeppelin's `Initializable` contract and applying the `initializer` modifier to `bridgeInit`. Ensure that `bridgeInit` can only be called once throughout the contract's lifecycle.


### `M-03` — High: Misapplication of `Cloneable` Pattern in Proxy Context  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `StandardArbERC20` contract inherits from `Cloneable`, which has a constructor that sets `isMasterCopy = true`. In a proxy pattern (like `ClonableBeaconProxy`), the constructor of the implementation contract is never executed for the proxy instances. Consequently, `isMasterCopy` will always retain its default value of `false` in all deployed proxy instances. While the `safeSelfDestruct` function is `internal` and thus not directly callable, this design flaw indicates a misunderstanding or misapplication of the `Cloneable` pattern within a proxy context. If future logic or an upgrade were to rely on `isMasterCopy` b

**Recommendation:** Re-evaluate the necessity and implementation of the `Cloneable` contract. If the `isMasterCopy` distinction is required, it must be managed via an initializer function that is called by the proxy, not a constructor. Alternatively, if `Cloneable`'s functionality is not critical for this specific proxy setup, consider removing it to simplify the codebase and avoid potential confusion.


### `L-01` — Low: Missing `_disableInitializers` Call in Implementation Constructor  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `StandardArbERC20` contract uses OpenZeppelin's upgradeable pattern, which typically requires calling `_disableInitializers()` in the constructor of the implementation contract. This prevents the implementation contract from being initialized directly, which could lead to storage collisions or unexpected behavior if a malicious actor were to call `_initialize` on the implementation directly, corrupting its storage layout for proxy instances (7.7 Upgrades).

**Recommendation:** Add `_disableInitializers()` to the constructor of `StandardArbERC20` (or its base `L2GatewayToken` or `aeERC20` if they have constructors) to ensure the implementation cannot be initialized directly.


### `L-02` — Low: `BytesParser.toString` Edge Case and Assembly Usage  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `BytesParser.toString` function contains complex logic for handling 32-byte inputs, including a check `if (input[31] != bytes1(0x00)) return (false, res);` which assumes null-termination for 32-byte strings. This could lead to incorrect parsing for non-null-terminated 32-byte strings. Additionally, the function uses an `assembly` block (`res := inputTruncated`) for converting `bytes` to `string`. While `string` is essentially `bytes`, direct assembly for this conversion can be less safe and harder to reason about than `abi.decode(inputTruncated, (string))` (7.2 Code Security).

**Recommendation:** Simplify the `BytesParser.toString` logic. Consider using `abi.decode(input, (string))` directly for all valid string lengths, allowing the EVM to handle padding and decoding. If custom truncation is strictly necessary, ensure the logic is robust and avoid direct assembly where higher-level Solidity constructs suffice for safety and readability.


### `I-01` — Informational: `TransferAndCallToken` Not Inherited  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `TransferAndCallToken` contract, which provides `transferAndCall` functionality, is included in the provided source code but `StandardArbERC20` does not inherit from it. This means the `transferAndCall` feature is not available in the deployed token. This is not a vulnerability but an observation regarding potential intended functionality that is not present (7.1 Architecture).

**Recommendation:** Clarify if `transferAndCall` functionality is intended for this token. If so, ensure `StandardArbERC20` (or one of its base contracts like `aeERC20`) inherits `TransferAndCallToken`.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x3e66...d2af`](https://arbiscan.io/address/0x3e6648c5a70a150a88bce65f4ad4d506fe15d2af) |
| **Network** | Arbitrum |
| **Price** | $0.0001027 |
| **24h Volume** | $37.5K |
| **Liquidity** | $131.4K |
| **Volume / Liquidity** | 0.3× |
| **Token Age** | 5y |
| **Top-10 Holders** | 80.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 441 buys / 449 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/arbitrum/0x8f93eaae544e8f5eb077a1e09c1554067d9e2ca8)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/spell-token-arb)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-27*
