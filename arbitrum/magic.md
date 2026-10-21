---
token: MAGIC
ticker: MAGIC
network: arbitrum
risk_score: 58
status: medium
date: 2026-08-31
---

# MAGIC (MAGIC) — Smart Contract Security Analysis | Arbitrum

> **Risk Score: 58/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/magic-arb)

---

## Audit Summary

The audit of the StandardArbERC20 implementation contract, used via a ClonableBeaconProxy, identified a High-severity access control vulnerability related to the initialization of cloned token instances. Additionally, Medium and Low severity issues were found concerning ERC20 standard compliance and parsing logic. The contract generally demonstrates good architectural patterns for an L2 bridged token, leveraging OpenZeppelin libraries and a beacon proxy for upgradeability. However, critical attention is required for the initialization process of new token clones to prevent unauthorized control.

> **Final Recommendation:** Prioritize implementing robust access control for the `bridgeInit` function to ensure only authorized entities can initialize new token clones. This is crucial for preventing unauthorized control over token minting and burning capabilities. Additionally, review the behavior of `name()`, `symbol()`, and `decimals()` to align with ERC20 standards, potentially by returning default values instead of reverting on parsing failures. Finally, refine the `BytesParser.toString` logic to handle edge cases more gracefully, ensuring consistent token metadata availability.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The StandardArbERC20 contract implements an L2 bridged ERC20 token, utilizing OpenZeppelin's upgradeable ERC20 standard and a `Cloneable` pattern for efficient deployment. Key strengths include the… |
| **Governance / Economics** | 1/10 | High | This contract primarily functions as an L2 token implementation and does not contain direct governance mechanisms or complex economic models. Its economic security is largely tied to the integrity of… |
| **Upgrades** | 1/10 | High | The contract is designed as an implementation for a ClonableBeaconProxy, enabling efficient deployment of multiple token instances and facilitating future upgrades via the beacon. The `_initialize`… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Beacon |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 55.2% |
| **Top-3 Unlocked** | ⚠️ 82.9% |

## Security Findings

_🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 2 Informational_

### `H-01` — Unprotected `bridgeInit` Allows Malicious Initialization of Clones  *(Severity: High · Status: Unresolved)*

The `bridgeInit` function, which serves as the initializer for each cloned token instance, is declared as `public` without any access control. While `L2GatewayToken._initialize` prevents re-initialization of state variables within a single clone, the *first* caller to `bridgeInit` on a newly deployed clone can set the `l2Gateway` and `l1Address`. A malicious actor could front-run the legitimate gateway deployment or initialization, setting themselves as the `l2Gateway`, thereby gaining unauthorized control over `bridgeMint` and `bridgeBurn` functions for that specific token instance. This compromises the integrity of the token supply for affected clones (7.3 Access Control, 7.2 Code Securit…

**Recommendation:** Implement an `onlyInitializing` or similar modifier to restrict calls to `bridgeInit` to a trusted entity (e.g., the deployer, a factory contract, or a designated initializer role). This ensures that only the intended party can configure the critical `l2Gateway` and `l1Address` for new token clones.


### `M-01` — ERC20 Standard Functions (`name`, `symbol`, `decimals`) Can Revert  *(Severity: Medium · Status: Unresolved)*

The `name()`, `symbol()`, and `decimals()` functions can revert if the corresponding `ignore` flags (`ignoreName`, `ignoreSymbol`, `ignoreDecimals`) are set to `true` during `bridgeInit`. These flags are set if the `BytesParser` fails to parse the provided `_data` for name, symbol, or decimals. This behavior deviates from the standard ERC20 interface, where these functions are expected to always return a value. Integrations relying on these functions might break if they do not handle reverts gracefully, leading to a denial of service for metadata retrieval (7.2 Code Security).

**Recommendation:** Consider returning default or empty values (e.g., empty string for name/symbol, 0 for decimals) instead of reverting when parsing fails. Alternatively, ensure robust validation of `_data` during `bridgeInit` to prevent these flags from being set unnecessarily, or provide a mechanism for a privileged role to correct the metadata if parsing initially fails.


### `L-01` — `BytesParser.toString` Edge Case for 32-Byte Strings  *(Severity: Low · Status: Unresolved)*

The `BytesParser.toString` function has specific logic for `input.length == 32`. If `input[31]` is not `bytes1(0x00)`, it returns `(false, res)`, indicating a parsing failure. This means a valid 32-byte string that happens to have a non-zero last byte (e.g., 'ABCDEFGHIJKLMNOPQRSTUVWXYZABCDEF') would be considered a parsing failure, leading to `ignoreName` or `ignoreSymbol` being set to `true`. This could cause the `name()` or `symbol()` functions to revert unnecessarily, even for valid inputs (7.2 Code Security).

**Recommendation:** Review the `BytesParser.toString` logic for 32-byte strings to ensure it correctly handles all valid string representations. If the intent is to treat 32-byte inputs as `bytes32` and only convert if they are null-padded, this should be clearly documented or handled differently to avoid false negatives for valid strings.


### `I-01` — Indirect `abi.decode` for String/Uint8 Parsing  *(Severity: Informational · Status: Unresolved)*

In `bridgeInit`, the `_data` is first `abi.decode`d into three `bytes` variables, which are then passed to `BytesParser.toString` and `BytesParser.toUint8`. If the `_data` is consistently encoded as `abi.encode(name, symbol, decimals)`, directly decoding to `(string, string, uint8)` might simplify the code. The current approach adds an extra parsing layer that handles specific byte representations (7.2 Code Security).

**Recommendation:** Document the expected encoding format for `_data`. If the `_data` is always `abi.encode(name, symbol, decimals)`, consider direct `abi.decode(_data, (string, string, uint8))` for simplicity. If the `bytes` inputs are expected to be arbitrary byte sequences requiring specific parsing logic (e.g., 32-byte fixed-length strings), the current approach is justified, but the parsing logic should be robust and well-documented.


### `I-02` — `TransferAndCallToken` Uses `extcodesize` for `isContract` Check  *(Severity: Informational · Status: Unresolved)*

The `isContract` function in `TransferAndCallToken` uses `extcodesize` to determine if an address is a contract. A known edge case with `extcodesize` is that it returns 0 during a contract's constructor execution. This means if `transferAndCall` is called to an address that is currently in its constructor, `isContract` would return `false`, and the `onTokenTransfer` callback would not be invoked (7.2 Code Security).

**Recommendation:** Be aware of this EVM quirk. For most scenarios, this is not an issue as `transferAndCall` is typically used with already deployed contracts. If interaction with contracts during their construction phase is a critical use case, alternative checks or design patterns might be necessary.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x539b...0342`](https://arbiscan.io/address/0x539bde0d7dbd336b79148aa742883198bbf60342) |
| **Network** | Arbitrum |
| **Price** | $0.04486 |
| **24h Volume** | $8.9K |
| **Liquidity** | $177.4K |
| **Volume / Liquidity** | 0.1× |
| **Token Age** | 4y |
| **Top-10 Holders** | 66.3% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 693 buys / 706 sells |

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

- [View on DexScreener](https://dexscreener.com/arbitrum/0xb7e50106a5bd3cf21af210a755f9c8740890a8c9)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/magic-arb)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-31*
