---
token: World Liberty Financial USD
ticker: USD1
network: bsc
risk_score: 77
status: high
date: 2026-09-19
---

# World Liberty Financial USD (USD1) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 77/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/world-liberty-financial-usd-bsc)

---

## Audit Summary

The StablecoinV2 contract, an upgradeable ERC-20 token, implements EIP-3009 for transfer authorizations and includes features for managing frozen accounts. The contract leverages OpenZeppelin's upgradeable patterns and security libraries. While the core EIP-3009 implementation and general code quality are robust, significant centralization risk exists due to the owner's ability to drain or reallocate funds from frozen accounts. Additionally, considerations for batch operation error handling and EIP-712 domain separator stability are noted.

> **Final Recommendation:** It is recommended to review the necessity and scope of the `drain` and `reallocate` functions, potentially implementing a timelock or further multi-signature approvals for these critical operations to mitigate centralization risks. For batch operations, consider whether silent error ignoring is the desired behavior or if a full revert on any failure is more appropriate. Furthermore, ensure that the `Stablecoin` parent contract adheres to robust upgradeability practices to prevent unforeseen storage or logic conflicts. Finally, consider using a more stable EIP-712 domain separator that is not tied to the token's mutable `name()` to ensure long-term signature validity across upgrades.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract demonstrates strong technical foundations by utilizing OpenZeppelin's battle-tested upgradeable contracts and `SafeERC20` for secure token interactions (7.2 Code Security). The… |
| **Governance / Economics** | 1/10 | High | The contract's owner, a 3/5 multisig, provides a good level of decentralization for administrative actions (7.5 Governance). However, the `drain` and `reallocate` functions grant the owner… |
| **Upgrades** | 1/10 | High | The contract is designed for upgradeability using OpenZeppelin's `TransparentUpgradeableProxy` pattern, correctly employing `_disableInitializers()` and `reinitializer` (7.7 Upgrades). The use of a… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Transparent |
| **Admin** | OZ ProxyAdmin → Multisig 3-of-5 |
| **Implementation** | ✅ Verified source |

## Security Findings

_🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 2 Informational_

### `H-01` — Centralized Control Over Frozen Account Funds  *(Severity: High · Status: Unresolved)*

The `drain` and `reallocate` functions allow the contract owner to transfer all funds from a frozen account to any specified address. While intended for emergency situations, this grants the owner significant centralized control over user assets in frozen accounts. A compromise of the owner's private keys or the multisig could lead to the unauthorized draining or reallocation of funds from all frozen accounts.

**Recommendation:** Implement additional safeguards for `drain` and `reallocate` functions. Consider requiring a multi-signature approval from a separate, highly secure committee, or introducing a timelock mechanism to allow users to react to pending fund movements. Clearly document the conditions under which these functions would be used.


### `M-01` — Batch Cancellation Silent Error Handling  *(Severity: Medium · Status: Unresolved)*

The `batchCancelAuthorization` function includes an `_ignoreErrors` parameter. If set to `true`, individual authorization cancellations that fail (e.g., due to invalid signatures or already used nonces) will be silently skipped, and the transaction will not revert. This behavior might be unexpected for users who assume all authorizations in a batch will be canceled or that the transaction will revert on any failure, potentially leading to confusion or incorrect off-chain state tracking.

**Recommendation:** Evaluate if silent error ignoring is the desired behavior. If not, consider removing the `_ignoreErrors` parameter or making the default behavior to revert on any individual failure. If `_ignoreErrors` is kept, ensure clear documentation and user interface communication about its implications, and consider emitting more granular events for each successful/failed cancellation within the batch.


### `L-01` — Undetermined Security of Parent Contract `Stablecoin`  *(Severity: Low · Status: Unresolved)*

The `StablecoinV2` contract inherits from `Stablecoin`, but the source code for `Stablecoin` was not provided for this audit. The security and upgradeability of `StablecoinV2` are directly dependent on the correctness, security, and proper upgradeability patterns of its parent contract. Any vulnerabilities, improper storage layouts, or upgrade issues within `Stablecoin` could directly impact `StablecoinV2`.

**Recommendation:** Conduct a full security audit of the `Stablecoin` parent contract to ensure it adheres to best practices, especially regarding upgradeability and storage management. Verify that its design does not introduce any hidden vulnerabilities or storage collision risks for `StablecoinV2`.


### `I-01` — EIP-712 Domain Separator Reliance on Mutable `name()`  *(Severity: Informational · Status: Unresolved)*

The EIP-712 domain separator is initialized using `__EIP712_init(name(), _EIP712_VERSION)`. The `name()` function, while typically static for ERC-20 tokens, could theoretically be changed in a future contract upgrade. If the token's `name()` were to change, it would invalidate all previously signed EIP-712 authorizations, as the domain separator would no longer match.

**Recommendation:** While `name()` is generally considered immutable for tokens, for maximum robustness and future-proofing, consider using a more stable identifier for the EIP-712 domain separator that is guaranteed not to change across upgrades, such as a hardcoded string or a constant that is not derived from a potentially mutable contract state.


### `I-02` — Lack of Event for Authorization Usage  *(Severity: Informational · Status: Unresolved)*

The `_setAuthorizationAsUsed` function, which marks an EIP-3009 authorization nonce as used, does not emit an explicit event. While `AuthorizationCanceled` is emitted when an authorization is canceled, there is no corresponding event when an authorization is successfully used (e.g., via `transferWithAuthorization` or `receiveWithAuthorization`). This makes it harder for off-chain systems to track the exact moment an authorization becomes invalid due to usage.

**Recommendation:** Consider emitting an event (e.g., `AuthorizationUsed(address indexed authorizer, bytes32 indexed nonce)`) within the `_setAuthorizationAsUsed` function. This would provide clearer visibility into the lifecycle of authorizations and facilitate more robust off-chain monitoring and indexing.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x8d0d...8b0d`](https://bscscan.com/address/0x8d0d000ee44948fc98c9b98a4fa4921476f08b0d) |
| **Network** | BNB Chain |
| **Price** | $1.0000 |
| **24h Volume** | $607.2K |
| **Liquidity** | $5.28M |
| **Volume / Liquidity** | 0.1× |
| **Token Age** | 1y |
| **Top-10 Holders** | 85.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 3678 buys / 3331 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x9c4ee895e4f6ce07ada631c508d1306db7502cce)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/world-liberty-financial-usd-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-19*
