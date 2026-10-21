---
token: Equilibria Token
ticker: EQB
network: arbitrum
risk_score: 55
status: medium
date: 2026-09-01
---

# Equilibria Token (EQB) — Smart Contract Security Analysis | Arbitrum

> **Risk Score: 55/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/equilibria-token-arb)

---

## Audit Summary

The audit of the `StandardArbERC20` implementation contract, used by `ClonableBeaconProxy` on Arbitrum, identified a critical access control vulnerability. This flaw allows any caller to initialize a new token proxy instance and designate themselves as the `l2Gateway`, granting unauthorized minting and burning capabilities. Additional findings include a medium-severity issue related to specific string parsing logic and a low-severity concern regarding the `selfdestruct` function. Addressing the critical vulnerability is paramount for the security and integrity of token instances.

> **Final Recommendation:** Immediately address the critical access control vulnerability in the `bridgeInit` function by implementing a robust authorization mechanism. This is paramount to prevent unauthorized control over token minting and burning. Review the `BytesParser.toString` logic to ensure it aligns with expected L1 bridge string encodings and consider a more flexible approach if necessary. Finally, evaluate the necessity of `safeSelfDestruct` and pin Solidity pragma versions for enhanced security and predictability.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 7/10 | Low | The technical architecture leverages OpenZeppelin's upgradeable ERC20 and a custom `Cloneable` pattern for Arbitrum bridge tokens, demonstrating a structured approach to token management. The… |
| **Governance / Economics** | 2/10 | High | The contract's economic model is that of a standard ERC20 token, with `bridgeMint` and `bridgeBurn` functions controlled by an `l2Gateway`. The `_initialize` function correctly prevents… |
| **Upgrades** | 1/10 | High | The contract is designed as an upgradeable implementation for a `ClonableBeaconProxy`, utilizing OpenZeppelin's upgradeable patterns and the `_initialize` function to manage state. The `Cloneable`… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Beacon |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🔴 1 Critical · 🟡 1 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `C-01` — Unrestricted `bridgeInit` Allows Arbitrary `l2Gateway` Assignment  *(Severity: Critical · Status: Unresolved)*

The `bridgeInit` function is declared as `public virtual` in `StandardArbERC20`. This function calls `L2GatewayToken._initialize`, which sets the `l2Gateway` state variable to `msg.sender`. This means any caller can deploy a new `StandardArbERC20` proxy instance, call `bridgeInit` on it, and become the `l2Gateway` for that specific token instance. The `l2Gateway` has exclusive control over `bridgeMint` and `bridgeBurn` functions, allowing an unauthorized entity to arbitrarily mint and burn tokens for that instance. While `_initialize` prevents re-initialization, the initial setup is completely uncontrolled, leading to a full compromise of token supply for any newly deployed instance.

**Recommendation:** Implement a robust access control mechanism for the `bridgeInit` function. This could involve restricting calls to a specific deployer address, a governance contract, or a multi-signature wallet. For beacon proxies, typically the beacon proxy factory or a designated deployer should be the only entity allowed to call `bridgeInit` on new instances to ensure the `l2Gateway` is a trusted address.


### `M-01` — `BytesParser.toString` Specific Behavior for 32-Byte Inputs  *(Severity: Medium · Status: Unresolved)*

The `BytesParser.toString` function implements specific logic for 32-byte inputs. If a 32-byte input is not null-terminated (i.e., `input[31] != bytes1(0x00)`), the function returns `(false, res)`. If it is null-terminated, it truncates trailing null bytes. For inputs of other lengths (non-zero, non-32), it directly `abi.decode`s. This specific handling of 32-byte strings might lead to unexpected parsing failures or truncated strings if the L1 bridge sends strings that do not conform to this exact expectation, even if they are valid UTF-8. While `ignoreName`/`ignoreSymbol` flags mitigate immediate reverts, it could result in tokens having incorrect or missing metadata.

**Recommendation:** Clarify and rigorously document the expected string encoding for 32-byte inputs from the L1 bridge. Consider if the `input[31] != bytes1(0x00)` check is truly necessary or if a more general string decoding approach (e.g., always `abi.decode` if possible, or a more robust null-termination check) would be safer. Ensure the L1 bridge adheres strictly to the expected format to prevent metadata inconsistencies.


### `L-01` — Presence of `selfdestruct` in `Cloneable` Contract  *(Severity: Low · Status: Unresolved)*

The `Cloneable` contract includes a `safeSelfDestruct` function. While it correctly prevents the master copy from being self-destructed (`require(!isMasterCopy)`), the presence of `selfdestruct` in a token contract, even if restricted to clones (proxy instances), can be a concern. If a clone is accidentally or maliciously self-destructed, all associated token balances and state for that specific token instance would be irretrievably lost, leading to permanent loss of funds for users holding that token.

**Recommendation:** Evaluate the necessity of the `safeSelfDestruct` function. If it is not strictly required for the protocol's lifecycle management or emergency procedures, consider removing it to eliminate the risk of accidental or malicious self-destruction of token instances. If it is deemed necessary, ensure extremely robust access control and operational procedures are in place for its invocation, potentially requiring a multi-signature approval or time-lock.


### `I-01` — Floating Pragma Version  *(Severity: Informational · Status: Unresolved)*

The contracts use a floating pragma `^0.6.11`. While this allows for minor bug fixes, it can lead to unexpected behavior if a newer compiler version introduces breaking changes or different opcode generation. Additionally, some imported contracts might have different pragma ranges (e.g., `ITransferAndCall` uses `>0.6.0 <0.8.0`), potentially leading to inconsistencies.

**Recommendation:** Pin the Solidity pragma to a specific version (e.g., `pragma solidity 0.6.11;`) to ensure consistent compilation behavior across deployments and upgrades. This practice helps prevent unexpected issues that might arise from compiler updates. Ensure all imported libraries and contracts are compatible with the chosen pinned version.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xbfbc...ad9c`](https://arbiscan.io/address/0xbfbcfe8873fe28dfa25f1099282b088d52bbad9c) |
| **Network** | Arbitrum |
| **Price** | $0.07414 |
| **24h Volume** | $4.3K |
| **Liquidity** | $184.6K |
| **Volume / Liquidity** | 0.0× |
| **Token Age** | 3y |
| **Top-10 Holders** | 57.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 82 buys / 58 sells |

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

- [View on DexScreener](https://dexscreener.com/arbitrum/0x69b545997bd6abc81cae39fe9bdc94d2242a0f92)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/equilibria-token-arb)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-01*
