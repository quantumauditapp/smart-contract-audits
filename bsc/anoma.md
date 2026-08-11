---
token: Anoma
ticker: XAN
network: bsc
risk_score: 81
status: critical
date: 2026-08-11
---

# Anoma (XAN) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 81/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/anoma-bsc)

---

## Audit Summary

This audit covers the TokenImplementation contract, which serves as the logic for a BridgeToken deployed via a BeaconProxy on the BSC network. The contract implements standard ERC-20 functionalities, including minting, burning, and EIP-712 permit. The code demonstrates good practices for upgradeability, such as state separation and an initializer. While the technical implementation is largely robust, the centralized control over token supply and metadata by the owner presents a significant governance and economic risk, albeit mitigated by the owner being a contract. A non-standard implementation of `transferFrom` was noted, along with minor informational findings.

> **Final Recommendation:** It is recommended to review the `transferFrom` implementation to align with standard ERC-20 practices, ensuring allowance checks and reductions occur before token transfers for improved efficiency and clarity. While centralized control is inherent to many bridge tokens, ensure the owner contract (0xb6f6d86a8f9879a9c87f643768d9efc38c1da6e7) is secured by a robust multi-signature wallet or a well-tested decentralized governance mechanism. Users of the `permit` function should be educated on the inherent front-running risks.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract exhibits a strong technical foundation (7.1 Architecture, 7.2 Code Security). It correctly implements ERC-20 standards and integrates EIP-712 permit functionality. State separation via… |
| **Governance / Economics** | 2/10 | High | The contract design (7.4 Economic, 7.5 Governance) grants significant centralized control to the `owner` address. The owner can `mint` and `burn` tokens, directly impacting the total supply and… |
| **Upgrades** | 1/10 | High | The contract is designed for upgradeability using the BeaconProxy pattern (7.7 Upgrades). The `initializer` modifier is correctly implemented to prevent re-initialization of the contract's state… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Beacon |
| **Implementation** | ✅ Verified source |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 78.6% |
| **Top-3 Unlocked** | ⚠️ 99.3% |

## Security Findings

_🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 2 Informational_

### `H-01` — Centralized Control over Token Supply and Metadata  *(Severity: High · Status: Unresolved)*

The `owner` address has exclusive control over critical functions such as `mint(address account_, uint256 amount_)`, `burn(address account_, uint256 amount_)`, and `updateDetails(string memory name_, string memory symbol_, uint64 sequence_)`. This allows the owner to arbitrarily increase or decrease the token supply, directly impacting its value, and to change the token's identifying metadata (name, symbol). While common for bridge tokens, this represents a significant centralization risk (7.4 Economic, 7.5 Governance).

**Recommendation:** Ensure the owner address (0xb6f6d86a8f9879a9c87f643768d9efc38c1da6e7) is controlled by a highly secure multi-signature wallet or a robust decentralized autonomous organization (DAO) to mitigate the risk of a single point of failure or compromise. Implement transparent processes for any minting, burning, or metadata update operations.


### `M-01` — Non-Standard `transferFrom` Logic  *(Severity: Medium · Status: Unresolved)*

The `transferFrom` function implements the token transfer (`_transfer`) before checking and reducing the allowance (`require(currentAllowance >= amount_)` and `_approve`). While the transaction will revert if the allowance is insufficient, this order deviates from the standard ERC-20 pattern where allowance is typically checked and reduced *before* or as part of the transfer. This can lead to higher gas costs for failed transactions, as the token transfer is attempted even when the allowance is insufficient (7.2 Code Security).

**Recommendation:** Refactor the `transferFrom` function to first check and reduce the allowance, and then perform the token transfer. This aligns with common ERC-20 implementations and improves gas efficiency for reverting transactions. For example, adopt the OpenZeppelin `_spendAllowance` pattern.


### `L-01` — EIP-712 Permit Front-Running Risk  *(Severity: Low · Status: Unresolved)*

The `permit` function, which allows users to sign approvals off-chain, is inherently susceptible to front-running. If a signed permit message is broadcast publicly (e.g., via a relayer or mempool) before being included in a transaction, a malicious actor could observe the message and submit their own transaction to execute the `permit` call, potentially causing the original transaction to revert or be exploited (7.2 Code Security). This is a known characteristic of the EIP-2612 standard and not a flaw in this specific implementation.

**Recommendation:** Educate users about the front-running risks associated with the `permit` function. Advise them to use private transaction relays or to be cautious when broadcasting signed messages publicly, especially for high-value transactions.


### `I-01` — Custom Ownership Implementation  *(Severity: Informational · Status: Unresolved)*

The contract implements its own ownership logic by storing the owner in `_state.owner` and using a custom `onlyOwner` modifier, rather than inheriting from OpenZeppelin's `Ownable` contract. While functionally similar, using a widely audited and standardized library like OpenZeppelin's `Ownable` is generally preferred for consistency, reduced risk of subtle bugs, and easier integration with ecosystem tools (7.2 Code Security).

**Recommendation:** Consider inheriting from OpenZeppelin's `Ownable` contract in `TokenState` or `TokenImplementation` for a more standardized and battle-tested ownership solution. If a custom implementation is necessary, ensure it has undergone thorough testing and review.


### `I-02` — Redundant `_initializePermitStateIfNeeded` Call in `permit`  *(Severity: Informational · Status: Unresolved)*

The `_initializePermitStateIfNeeded()` function is called at the beginning of every `permit` function invocation. While its internal logic prevents unnecessary state updates if the cached values are current, calling it repeatedly adds a minor, albeit negligible, gas overhead. This function is primarily intended for initial setup or when metadata details are updated (7.2 Code Security).

**Recommendation:** Consider removing the `_initializePermitStateIfNeeded()` call from the `permit` function, as the permit domain separator is typically stable after initialization and metadata updates. The `_domainSeparatorV4()` function already handles re-computation if `block.chainid` or `address(this)` changes, making the explicit call in `permit` redundant for most cases.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x7427...a07f`](https://bscscan.com/address/0x7427bd9542e64d1ac207a540cfce194b7390a07f) |
| **Network** | BNB Chain |
| **Price** | $0.01227 |
| **24h Volume** | $2.10M |
| **Liquidity** | $473.4K |
| **Volume / Liquidity** | 4.4× |
| **Token Age** | 10mo |
| **Top-10 Holders** | 84.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 14204 buys / 14669 sells |

## Security Flags (1/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x049f1009bc8c5d0048732fe2f95c27c240214634)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/anoma-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-11*
