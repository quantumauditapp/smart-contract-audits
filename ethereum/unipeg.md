---
token: Unipeg
ticker: UPEG
network: ethereum
risk_score: 24
status: medium
date: 2026-07-31
---

# Unipeg (UPEG) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 24/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/unipeg-eth)

---

## Audit Summary

The Unipeg contract implements an ERC20 token with integrated NFT (Upeg) syncing logic. The audit identified a critical reentrancy/logic flaw in the token-NFT synchronization mechanism, a high-severity economic issue leading to potential decoupling of token and NFT balances, and medium-severity centralization risks. While access controls are generally well-defined, the complex interaction between ERC20 and Upeg transfers introduces significant security challenges.

> **Final Recommendation:** It is critical to address the reentrancy/logic flaw in the ERC20-Upeg synchronization to prevent potential exploits and ensure consistent state. The economic model's decoupling issue also requires immediate attention to maintain the integrity of the token-NFT link. Consider implementing a more robust and explicit state machine for managing the synchronization, possibly with reentrancy guards or clearer separation of concerns between the ERC20 and Upeg transfer hooks. Thoroughly review the `Upeg.sol` contract's implementation, especially its transfer hooks, to ensure it does not exacerbate or introduce new vulnerabilities in conjunction with `Unipeg.sol`.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 7/10 | Low | The technical architecture (7.1) presents a complex dual-token system where ERC20 and NFT (Upeg) balances are intended to be synchronized. Code security (7.2) is significantly impacted by a critical… |
| **Governance / Economics** | 5/10 | Medium | The economic model (7.4) attempts to link ERC20 token holdings with Upeg NFT ownership, but a high-severity flaw in the syncing logic allows for a decoupling where actual Upeg counts can fall below… |
| **Upgrades** | 8/10 | Low | The Unipeg contract is not designed with an upgrade mechanism (7.7), meaning its logic is immutable once deployed. This eliminates upgrade-related risks but requires thorough pre-deployment auditing.… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 84.7% |
| **Top-3 Unlocked** | ⚠️ 99.7% |

## Security Findings

_🔴 1 Critical · 🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `C-01` — Critical Reentrancy/Logic Flaw in Upeg-ERC20 Sync  *(Severity: Critical · Status: Unresolved)*

The `Unipeg` contract exhibits a critical circular dependency between ERC20 token transfers and Upeg NFT transfers. When an ERC20 transfer occurs, the `_afterTokenTransfer` hook calls `_onTokenTransfer` to synchronize Upegs. If `_onTokenTransfer` determines that Upegs need to be moved (e.g., in a user-to-user transfer), it calls `_moveUpegs`, which in turn calls `_transferUpeg` (from the inherited `Upeg.sol` contract). The `_transferUpeg` function, as an override, then triggers `_afterUpegTransferred` in `Unipeg.sol`. Crucially, `_afterUpegTransferred` then executes an internal ERC20 transfer via `_transfer(from, to, UNIT_PER_UPEG)`. This creates a reentrant call to the ERC20 transfer mecha…

**Recommendation:** Refactor the Upeg-ERC20 synchronization logic to break the circular dependency. The `_afterUpegTransferred` and `_afterUpegsListTransferred` functions should not trigger new ERC20 transfers if the Upeg transfer was initiated by an existing ERC20 transfer. Instead, these hooks should only handle the ERC20 side if the Upeg transfer was initiated independently (e.g., by a direct call to `_transferUpeg` not originating from `_onTokenTransfer`). Consider using a reentrancy guard or a flag to prevent…


### `H-01` — Economic Decoupling of ERC20 and Upeg Balances  *(Severity: High · Status: Unresolved)*

The logic in `_onTokenTransfer` for calculating `from_remove_cnount` can lead to a permanent decoupling of ERC20 token balances and Upeg NFT counts. The calculation `from_remove_cnount = from_count > from_max_allowed ? from_count - from_max_allowed : 0;` means that if an account's actual Upeg count (`from_count`) is already less than the expected Upeg count derived from its ERC20 balance (`balanceOf(from) / UNIT_PER_UPEG`), no Upegs will be removed or burned when ERC20 tokens are transferred out. This allows users to reduce their ERC20 balance without affecting their Upeg count, effectively 'hiding' Upegs or creating a state where the total number of Upegs in circulation is significantly le…

**Recommendation:** Re-evaluate the synchronization logic to ensure a consistent 1:1 relationship between `UNIT_PER_UPEG` tokens and one Upeg NFT. Implement a mechanism to actively reconcile discrepancies where `OwnerUpegsCount` is less than `balanceOf / UNIT_PER_UPEG`. This might involve burning excess Upegs when tokens are transferred out, or preventing token transfers if they would lead to an invalid Upeg state. The goal should be to prevent a scenario where users can hold ERC20 tokens without the corresponding…


### `M-01` — Centralization Risk with Owner and Hook Control  *(Severity: Medium · Status: Unresolved)*

The contract's owner has significant control over critical system parameters. The owner can set the `hook` address via `setHook()`. This `hook` address is then the only entity authorized to call `start()`, which sets the crucial `pool` address and enables the token's core functionality (Upeg minting/burning). A compromised owner account or a malicious owner could set a malicious `hook` address, which could then set a malicious `pool` address, leading to potential manipulation of the Upeg minting/burning process, unauthorized token mints, or other forms of economic exploitation.

**Recommendation:** While `Ownable` is a standard pattern, consider implementing a multi-signature wallet for the owner address to reduce the risk of a single point of failure. For highly critical functions like `setHook`, consider a time-locked or multi-step ownership transfer process to allow for community review or intervention. Clearly document the responsibilities and potential impact of the `owner` and `hook` roles.


### `L-01` — Precision Loss in Upeg Count Calculations  *(Severity: Low · Status: Unresolved)*

The calculations for Upeg counts, such as `amount / UNIT_PER_UPEG` in `_mintUpegs` and `balanceOf(addr) / UNIT_PER_UPEG` for `from_max_allowed` and `to_max_allowed`, use integer division. This truncates any remainder, meaning that if an account holds, for example, `1.9 * UNIT_PER_UPEG` tokens, it is only considered to own 1 Upeg. This results in a slight discrepancy where fractional Upeg equivalents are not accounted for, potentially leading to minor economic inefficiencies or user confusion regarding their exact Upeg entitlement based on their token balance.

**Recommendation:** This is a design choice, but it should be clearly communicated to users. If a more precise representation is desired, consider alternative mechanisms for linking tokens and Upegs that can handle fractional amounts, or explicitly state that Upegs are only granted/counted in whole `UNIT_PER_UPEG` increments. Ensure that the implications of this precision loss are fully understood and accepted within the project's economic model.


### `I-01` — Undisclosed Dependency on `Upeg.sol` Implementation  *(Severity: Informational · Status: Unresolved)*

The `Unipeg.sol` contract heavily relies on the internal implementation details of the `Upeg.sol` contract, which was not provided for this audit. Functions like `_mintUpeg`, `_burnUpeg`, `_transferUpeg`, `OwnerUpegsCount`, and `OwnerUpeg` are critical for the core logic of `Unipeg.sol`. The security and correctness of the entire system are therefore directly dependent on the robustness, reentrancy-safety, and bug-free nature of the `Upeg.sol` contract. Any vulnerabilities or unexpected behaviors within `Upeg.sol` could directly compromise `Unipeg.sol`.

**Recommendation:** Conduct a full audit of the `Upeg.sol` contract, paying close attention to its internal state management, transfer mechanisms, and any external interactions. Ensure that `Upeg.sol` adheres to best security practices, especially regarding reentrancy and access control, as its interactions with `Unipeg.sol` are highly sensitive. Provide the source code for `Upeg.sol` for a comprehensive security assessment.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x44b2...5505`](https://etherscan.io/address/0x44b28991b167582f18ba0259e0173176ca125505) |
| **Network** | Ethereum |
| **Price** | $443.0670 |
| **24h Volume** | $911.4K |
| **Liquidity** | $1.15M |
| **Volume / Liquidity** | 0.8× |
| **Token Age** | 3mo |
| **Top-10 Holders** | 17.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 709 buys / 586 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x94af294207a2c592c08a39c82a7df42a18613d986eeb520b7164fe9ccd66a000)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/unipeg-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-07-31*
