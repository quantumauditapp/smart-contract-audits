---
token: Tether Gold
ticker: XAUT
network: bsc
risk_score: 85
status: critical
date: 2026-08-11
---

# Tether Gold (XAUT) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 85/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/tether-gold-bsc)

---

## Audit Summary

The audit covers the TetherTokenV2 contract, an upgradeable ERC20 token with EIP-3009 authorization and a blocked list feature. The contract utilizes OpenZeppelin's upgradeable patterns and access control. Key findings include significant centralized control by the owner (a multisig), potential gas limit issues for batch transfers, and an incomplete `_permit` function in the provided source. The upgradeability mechanism is standard and well-implemented.

> **Final Recommendation:** It is crucial for users to be fully aware of the significant centralized control exercised by the contract owner, including the ability to mint, burn, block users, and confiscate funds. Ensure the full and verified source code for all functionalities, especially `_permit`, is available for comprehensive auditing. Consider implementing mechanisms to mitigate potential gas limit issues for `multiTransfer` if large batch operations are anticipated. Maintain clear documentation regarding the owner's capabilities and the implications for token holders.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 4/10 | Medium | The contract leverages OpenZeppelin's upgradeable ERC20, Ownable, and Permit standards, enhancing code security and maintainability (7.2 Code Security). It implements EIP-3009 for signature-based… |
| **Governance / Economics** | 1/10 | High | The contract exhibits a high degree of centralization, with the owner (a 3/5 multisig) possessing extensive control over the token's economic parameters and user funds (7.4 Economic, 7.5 Governance).… |
| **Upgrades** | 1/10 | High | The contract utilizes the TransparentUpgradeableProxy pattern from OpenZeppelin, a well-established and secure upgrade mechanism (7.7 Upgrades). The implementation contract correctly inherits from… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Transparent |
| **Admin** | OZ ProxyAdmin → Multisig 3-of-5 |
| **Implementation** | ✅ Verified source |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | 49.4% |
| **Top-3 Unlocked** | 59.5% |

## Security Findings

_🔴 1 Critical · 🟠 1 High · 🟡 2 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `C-01` — Centralized Control and Owner Privileges  *(Severity: Critical · Status: Unresolved)*

The contract owner (a 3/5 multisig) possesses extensive centralized control over the token supply and user funds. The owner can `mint` new tokens, `redeem` (burn) tokens from their own balance, `block` any address, and `destroyBlockedFunds` from blocked users. This level of control allows the owner to arbitrarily increase/decrease token supply and confiscate user assets, representing a significant economic and governance risk (7.3 Access Control, 7.4 Economic, 7.5 Governance).

**Recommendation:** Clearly communicate the extent of owner privileges to all users and stakeholders. Consider implementing time-locks or community governance for critical functions like minting, burning, or fund destruction to decentralize control over time. Ensure robust operational security for the multisig wallet controlling the owner address.


### `H-01` — Potential Gas Limit Exceeded in `multiTransfer`  *(Severity: High · Status: Unresolved)*

The `multiTransfer` function iterates through arrays of recipients and values to perform multiple `transfer` calls. If the `_recipients` and `_values` arrays are excessively large, the transaction could exceed the block gas limit, causing the transaction to fail or become unusable for large batch operations (7.2 Code Security).

**Recommendation:** Implement a mechanism to limit the number of transfers per transaction, or provide a way to process transfers in smaller batches. Alternatively, consider using a more gas-efficient batch transfer pattern if large-scale operations are a primary use case.


### `M-01` — Truncated `_permit` Function Source Code  *(Severity: Medium · Status: Unresolved)*

The provided source code for the `_permit` function in `TetherTokenV2.sol` is truncated. This prevents a complete security analysis of the ERC20 Permit functionality, which is critical for gasless transactions and involves signature verification (7.2 Code Security).

**Recommendation:** Provide the complete and verified source code for the `_permit` function to allow for a thorough security audit of its implementation, especially regarding signature validation, nonce management, and deadline checks.


### `M-02` — Owner Bypass for Blocked `from` Address in `_beforeTokenTransfer`  *(Severity: Medium · Status: Unresolved)*

The `_beforeTokenTransfer` hook contains a condition `require(!isBlocked[from] \|\| msg.sender == owner(), 'TetherToken: from is blocked');`. This allows the contract owner to bypass the blocked list check and transfer tokens *from* a blocked address. While consistent with the `destroyBlockedFunds` functionality, this grants the owner additional power to move funds from blocked accounts without explicitly burning them, which might not be immediately obvious to users (7.3 Access Control).

**Recommendation:** Clearly document this specific owner capability in user-facing materials and internal documentation. Ensure that the implications of this bypass are fully understood by all stakeholders, as it provides a mechanism for the owner to reallocate funds from blocked users.


### `L-01` — Mixed Solidity Pragma Directives  *(Severity: Low · Status: Unresolved)*

The `EIP3009.sol` file uses `pragma solidity >=0.6.12 <0.9.0;`, while `TetherToken.sol` and `TetherTokenV2.sol` use `pragma solidity 0.8.4;`. Although `0.8.4` falls within the specified range, using consistent and explicit pragma directives across all files is a best practice for clarity and to prevent unexpected compiler behavior with future versions (7.2 Code Security).

**Recommendation:** Unify the pragma directives to `pragma solidity 0.8.4;` across all contract files for consistency and to explicitly state the intended compiler version.


### `I-01` — Unused `isTrusted` Mapping  *(Severity: Informational · Status: Unresolved)*

The `isTrusted` mapping is declared in `TetherToken.sol` but is not used anywhere in the provided contract code. This variable consumes storage space without serving any functional purpose (7.2 Code Security).

**Recommendation:** Remove the `isTrusted` mapping if it is not intended for future use, or implement its intended functionality. If it's a placeholder for future features, consider adding a comment to explain its purpose.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x21ca...a3bf`](https://bscscan.com/address/0x21caef8a43163eea865baee23b9c2e327696a3bf) |
| **Network** | BNB Chain |
| **Price** | $4,353.3200 |
| **24h Volume** | $3.78M |
| **Liquidity** | $1.34M |
| **Volume / Liquidity** | 2.8× |
| **Token Age** | 4mo |
| **Top-10 Holders** | 95.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 18609 buys / 12487 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xc655e1a100a084d9ac91c269b0a7cb0e62263fcf)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/tether-gold-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-11*
