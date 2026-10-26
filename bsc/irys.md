---
token: Irys
ticker: IRYS
network: bsc
risk_score: 52
status: medium
date: 2026-09-28
---

# Irys (IRYS) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 52/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/irys-bsc)

---

## Audit Summary

The IrysOFT contract, an upgradeable LayerZero Omnichain Fungible Token, was audited for security vulnerabilities. A critical vulnerability was identified in the `initialize` function, which would cause the contract's deployment to revert due to a double initialization of the Ownable component. This prevents the contract from being properly set up. Other findings include minor optimizations and best practice recommendations. The contract leverages well-audited OpenZeppelin and LayerZero libraries, and features a robust access control model with a multisig owner.

> **Final Recommendation:** The critical initialization bug (C-01) must be addressed immediately to enable the contract's successful deployment and operation. It is recommended to remove the redundant `__Ownable_init` call from the `initialize` function. Additionally, consider implementing the suggested informational improvements for enhanced clarity and maintainability. A thorough re-test of the initialization process after applying the fix is crucial.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract is built upon established OpenZeppelin and LayerZero libraries, providing a solid foundation for its architecture (7.1). It incorporates standard security features like pausable… |
| **Governance / Economics** | 3/10 | High | The contract's economic model (7.4) is straightforward, with a fixed token supply after initialization and no complex rebase or fee mechanisms. Governance (7.5) is robust, with ownership managed by a… |
| **Upgrades** | 2/10 | High | The contract implements the UUPS upgradeability pattern (7.7), which is a secure and widely adopted standard. The `_authorizeUpgrade` function is correctly restricted to the `onlyOwner` modifier… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Uups |
| **Implementation** | ✅ Verified source |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 1 Medium · 🟢 1 Low · ⚪ 2 Informational_

### `M-01` — Initialization Revert Due to Double Ownable Initialization  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `initialize` function calls `__Ownable_init(_delegate)` directly, and then subsequently calls `__OFT_init(_name, _symbol, _delegate)`. The `__OFT_init` function, inherited from `OFTUpgradeable`, internally calls `__Ownable_init` as part of its initialization chain. This results in `__Ownable_init` being called twice within the same `initialize` transaction. OpenZeppelin's `OwnableUpgradeable` prevents re-initialization by checking an internal `_initialized` flag, causing the second call to revert. Consequently, the `initialize` function will always fail, making the contract undeployable and unusable.

**Recommendation:** Remove the direct call to `__Ownable_init(_delegate)` from the `initialize` function. The `__OFT_init` function already handles the proper initialization of the `Ownable` component, ensuring the owner is set correctly. This will resolve the double initialization issue and allow the contract to be initialized successfully.


### `L-01` — Unnecessary `_totalSupply` Check  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `initialize` function includes a check `if (_totalSupply > type(uint256).max / 2) revert IrysOFT__SupplyTooLarge();`. While this check is often used to prevent multiplication overflows (e.g., if `_totalSupply` were to be doubled), there are no such operations in the current contract that would cause an overflow with `_totalSupply` itself. This check is overly cautious and not strictly necessary for the current logic.

**Recommendation:** Consider removing this check unless a specific future operation is planned that would justify its presence. While harmless, it adds minor complexity without a clear current benefit.


### `I-01` — Hardcoded String Length Limits  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `initialize` function hardcodes maximum length limits for `_name` (50 characters) and `_symbol` (20 characters). While these limits are reasonable, hardcoding them makes them inflexible. If future requirements necessitate different lengths, the contract would require an upgrade.

**Recommendation:** Consider defining `MAX_NAME_LENGTH` and `MAX_SYMBOL_LENGTH` as `immutable` constants or, if dynamic control is desired, as owner-configurable state variables. This would improve flexibility without compromising security.


### `I-02` — Missing Event for `acceptOwnership` Completion  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract emits `OwnershipTransferStarted` and `OwnershipTransferCanceled` events for the two-step ownership transfer process. However, the `acceptOwnership` function, which finalizes the transfer, does not emit a specific event to signal its completion. While the underlying `_transferOwnership` function (from Ownable) emits `OwnershipTransferred`, a dedicated event for `acceptOwnership` would provide clearer off-chain visibility into the full lifecycle of the two-step transfer.

**Recommendation:** Consider adding a specific event, such as `OwnershipAccepted(address indexed newOwner)`, within the `acceptOwnership` function after the `_transferOwnership` call. This would enhance transparency and ease of monitoring for off-chain systems.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x9115...035d`](https://bscscan.com/address/0x91152b4ef635403efbae860edd0f8c321d7c035d) |
| **Network** | BNB Chain |
| **Price** | $0.01702 |
| **24h Volume** | $2.16M |
| **Liquidity** | $407.0K |
| **Volume / Liquidity** | 5.3× |
| **Token Age** | 9mo |
| **Top-10 Holders** | 90.5% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 13349 buys / 15251 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x73de8b8d37fac1afe156f6533788a0eff197d636)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/irys-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-28*
