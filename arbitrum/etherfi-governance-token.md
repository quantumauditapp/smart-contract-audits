---
token: ether.fi governance token
ticker: ETHFI
network: arbitrum
risk_score: 58
status: medium
date: 2026-09-12
---

# ether.fi governance token (ETHFI) — Smart Contract Security Analysis | Arbitrum

> **Risk Score: 58/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/etherfi-governance-token-arb)

---

## Audit Summary

The audit of the EthfiL2Token contract identified a critical storage collision between `Ownable2StepUpgradeable` and `AccessControlEnumerableUpgradeable` during initialization. This flaw corrupts the contract owner's address, rendering the contract unmanageable and unupgradeable by the intended owner. Additionally, the `burnFrom` function, part of the `IMintableBurnable` interface, is explicitly reverted, which may break LayerZero's cross-chain functionality. Centralized control over minting and pausing also presents inherent risks. Immediate action is required to address the critical storage collision.

> **Final Recommendation:** The critical storage collision issue must be addressed immediately. This requires a redeployment with a corrected initialization logic or a careful re-evaluation of the inheritance structure to prevent storage slot conflicts. Additionally, the explicit reversion of `burnFrom` should be reviewed in the context of LayerZero's `IMintableBurnable` interface requirements to ensure cross-chain functionality is not compromised. Consider implementing a timelock for critical administrative actions to enhance security and decentralization.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 4/10 | Medium | The contract leverages well-audited OpenZeppelin libraries for its ERC-20, upgradeability (UUPS), and access control features (Ownable2Step, AccessControlEnumerable, Pausable). The custom minter role… |
| **Governance / Economics** | 4/10 | Medium | The contract implements a centralized governance model where a single owner (expected to be a multisig) controls critical functions such as setting the minter, pausing transfers, and authorizing… |
| **Upgrades** | 1/10 | High | The contract utilizes the UUPS upgradeability pattern, which is a robust and widely adopted standard for upgradeable contracts (7.7 Upgrades). The `_authorizeUpgrade` function correctly restricts… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Uups |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | 26.8% |
| **Top-3 Unlocked** | 52.5% |

## Security Findings

_🔴 1 Critical · 🟠 1 High · 🟡 2 Medium · ⚪ 1 Informational_

### `C-01` — Critical Storage Collision in Initialization  *(Severity: Critical · Status: Unresolved)*

The contract suffers from a critical storage collision due to the inheritance order and initialization of `Ownable2StepUpgradeable` and `AccessControlEnumerableUpgradeable`. `Ownable2StepUpgradeable` uses storage slot 0 for its `_owner` variable, while `AccessControlEnumerableUpgradeable` also uses slot 0 for its `_roles` mapping. When `initializeV2()` is called after `initialize()`, the `__AccessControlEnumerable_init()` function overwrites the `_owner` address set by `__Ownable_init()`. This corrupts the `owner()` address, making the contract unmanageable and unupgradeable by the intended owner, as functions relying on `onlyOwner` (e.g., `setMinter`, `_authorizeUpgrade`) will fail or be c…

**Recommendation:** To resolve this, ensure that `Ownable2StepUpgradeable` and `AccessControlEnumerableUpgradeable` do not collide on storage slots. The recommended approach is to use OpenZeppelin's `UUPSUpgradeable` with `ERC1967Proxy` and then carefully manage the inheritance and initialization order, or use a single access control mechanism (e.g., `AccessControl` only) if `Ownable`'s specific features are not strictly required. If both are needed, ensure they are initialized in a way that respects their storage…


### `H-01` — Unimplemented `burnFrom` for LayerZero Interface  *(Severity: High · Status: Unresolved)*

The contract implements the `IMintableBurnable` interface from LayerZero but explicitly reverts the `burnFrom(address, uint256)` function with `revert UnimplementedMethod()`. If LayerZero's Omnichain Fungible Token (OFT) implementation or other integrated systems rely on the `burnFrom` function for cross-chain transfers or other operations, this explicit reversion will cause critical failures in those functionalities. This directly impacts the expected behavior of the token within the LayerZero ecosystem. This impacts 7.6 External.

**Recommendation:** Clarify with the LayerZero integration team whether the `burnFrom` function is expected to be functional for the specific OFT implementation. If it is required, implement the `burnFrom` function with appropriate access control (e.g., `onlyMinter` or `onlyRole`) and logic consistent with the token's burning mechanism. If it is not required, consider removing the `IMintableBurnable` interface implementation if it's not strictly necessary, or document this design choice clearly.


### `M-01` — Centralized Control of Minter Role  *(Severity: Medium · Status: Unresolved)*

The `minter` address has the capability to mint an unlimited supply of tokens via the `mint` function, which is protected by the `onlyMinter` modifier. The `setMinter` function, which changes this critical role, is restricted to the contract owner. This centralized control over token supply introduces a single point of failure and a significant economic risk, as a compromised owner or minter address could lead to arbitrary token inflation. This impacts 7.4 Economic and 7.5 Governance.

**Recommendation:** While common for L2 bridge tokens, consider implementing additional safeguards for the `setMinter` function, such as a timelock or a multi-signature approval process, to reduce the risk associated with a single point of control. Regularly review and secure the private keys or multisig setup controlling the owner and minter addresses.


### `M-02` — Centralized Pause/Unpause Functionality  *(Severity: Medium · Status: Unresolved)*

The contract includes `pause` and `unpause` functions, controlled by `PAUSER_ROLE` and `UNPAUSER_ROLE` respectively. These roles allow designated addresses to halt all token transfers and other `whenNotPaused` operations. While useful for emergency situations (e.g., mitigating exploits), this centralized control can lead to a denial-of-service for all token holders if misused or compromised, impacting liquidity and user access. This impacts 7.8 Operations and 7.5 Governance.

**Recommendation:** Ensure that the `PAUSER_ROLE` and `UNPAUSER_ROLE` are assigned to highly secure, multi-signature wallets or a robust governance mechanism. Implement clear operational procedures for invoking pause/unpause functionality. Consider adding a timelock for the `unpause` function to provide a window for community review before resuming operations, if appropriate for the project's governance model.


### `I-01` — `decreaseAllowance` with `unchecked` block  *(Severity: Informational · Status: Resolved)*

The `decreaseAllowance` function uses an `unchecked` block for the subtraction `currentAllowance - _decreaseAmount` after a `require(currentAllowance >= _decreaseAmount)` check. This is a standard and safe optimization to save gas by avoiding redundant overflow/underflow checks by the EVM. This impacts 7.2 Code Security.

**Recommendation:** No action is required. This is a good practice for gas optimization when safety checks are already in place.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x7189...dc27`](https://arbiscan.io/address/0x7189fb5b6504bbff6a852b13b7b82a3c118fdc27) |
| **Network** | Arbitrum |
| **Price** | $0.7356 |
| **24h Volume** | $71.1K |
| **Liquidity** | $138.4K |
| **Volume / Liquidity** | 0.5× |
| **Token Age** | 1y |
| **Top-10 Holders** | 69.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 817 buys / 753 sells |

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

- [View on DexScreener](https://dexscreener.com/arbitrum/0x0f143fc50d6c71fee95d6ec1030e62d788507b84)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/etherfi-governance-token-arb)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-12*
