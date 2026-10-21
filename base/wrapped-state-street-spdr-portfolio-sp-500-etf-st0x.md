---
token: Wrapped State Street SPDR Portfolio S&P 500 ETF ST0x
ticker: WTSPYM
network: base
risk_score: 64
status: medium
date: 2026-09-06
---

# Wrapped State Street SPDR Portfolio S&P 500 ETF ST0x (WTSPYM) — Smart Contract Security Analysis | Base

> **Risk Score: 64/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/wrapped-state-street-spdr-portfolio-sp-500-etf-st0x-base)

---

## Audit Summary

The StoxWrappedTokenVault contract, serving as an ERC-4626 implementation behind a BeaconProxy, has been audited. The contract is minimal, primarily relying on well-vetted OpenZeppelin upgradeable libraries. No critical or high-severity vulnerabilities were identified. Minor issues include potential compatibility challenges with non-standard ERC-20 assets and an unused initialization function. The upgradeability mechanism is correctly implemented.

> **Final Recommendation:** It is recommended to thoroughly test the vault with the specific underlying ERC-20 asset intended for deployment, paying close attention to any non-standard behaviors of the asset. Implement robust monitoring for the vault's operations and the underlying asset's health. Consider adding explicit checks or warnings if non-standard ERC-20 tokens are to be supported in the future.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 7/10 | Low | The contract (7.1 Architecture) is a straightforward ERC-4626 vault implementation, inheriting extensively from OpenZeppelin's battle-tested upgradeable contracts. This significantly reduces the… |
| **Governance / Economics** | 1/10 | High | The contract implements a standard ERC-4626 vault (7.4 Economic) without introducing complex economic models, fees, or governance mechanisms (7.5 Governance). Its economic behavior is primarily… |
| **Upgrades** | 1/10 | High | The contract is designed as an upgradeable implementation for a BeaconProxy (7.7 Upgrades), correctly utilizing OpenZeppelin's `Upgradeable` pattern. The `_disableInitializers()` function in the… |

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

_🟢 1 Low · ⚪ 2 Informational_

### `L-01` — Potential for Non-Standard ERC-20 Asset Issues  *(Severity: Low · Status: Unresolved)*

The `StoxWrappedTokenVault` is an ERC-4626 vault that wraps an underlying ERC-20 asset. While OpenZeppelin's ERC-4626 implementation is robust, certain non-standard ERC-20 tokens (e.g., rebase tokens, tokens with transfer fees, tokens that revert on zero-value transfers, tokens with non-boolean return values for `transfer`/`transferFrom`) can cause unexpected behavior, accounting discrepancies, or loss of funds within an ERC-4626 vault. The current contract does not implement specific safeguards or checks for such tokens, relying solely on the standard ERC-20 interface.

**Recommendation:** Before deploying with a specific asset, thoroughly review the underlying ERC-20 token's contract for any non-standard behaviors. If such behaviors are identified, consider implementing custom logic within the vault (e.g., by overriding `_deposit`, `_withdraw`, `_mint`, `_redeem` functions) to handle them gracefully, or restrict the vault to only support standard ERC-20 tokens. Comprehensive testing with the chosen asset is crucial.


### `I-01` — Unused/Decoy `initialize(address)` Function  *(Severity: Informational · Status: Unresolved)*

The contract includes an `initialize(address asset) external pure returns (bytes32)` function that immediately reverts with `InitializeSignatureFn()`. This function is marked `pure`, meaning it cannot modify state, and its immediate revert makes it harmless. However, its presence alongside the actual `initialize(bytes calldata data)` function could be confusing or misleading for developers or auditors.

**Recommendation:** Consider removing the unused `initialize(address asset)` function to improve code clarity and reduce potential confusion. If it serves a specific, non-obvious purpose (e.g., preventing a specific signature collision), add a comment explaining its intent.


### `I-02` — Reliance on External `ICloneableV2` Interface  *(Severity: Informational · Status: Unresolved)*

The contract implements the `ICloneableV2` interface and returns `ICLONEABLE_V2_SUCCESS` from its `initialize` function. This indicates that the contract is designed to be deployed via a factory that expects this specific interface and return value. While not a vulnerability in the vault itself, this is an important architectural dependency that should be understood for proper deployment, management, and interaction with the vault instances.

**Recommendation:** Ensure that the factory deploying instances of this vault is correctly configured to interact with the `ICloneableV2` interface and handles the expected return value. Document this architectural dependency clearly for future development and operational teams.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x31c2...c2d8`](https://basescan.org/address/0x31c2c14134e6e3b7ef9478297f199331133fc2d8) |
| **Network** | Base |
| **Price** | $303.2300 |
| **24h Volume** | $164.5K |
| **Liquidity** | $744.7K |
| **Volume / Liquidity** | 0.2× |
| **Token Age** | 1d |
| **Top-10 Holders** | 98.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 568 buys / 1066 sells |

## Security Flags (1/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Sources

- [View on DexScreener](https://dexscreener.com/base/0xc2dd131e210679afff1749c7f5d219bf87e9dd436b0bdd48a6bd27075b205ac3)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/wrapped-state-street-spdr-portfolio-sp-500-etf-st0x-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-06*
