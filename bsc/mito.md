---
token: MITO
ticker: MITO
network: bsc
risk_score: 79
status: high
date: 2026-09-02
---

# MITO (MITO) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 79/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/mito-bsc)

---

## Audit Summary

The audit of the HypERC20 contract, an upgradeable ERC20 token integrated with the Hyperlane cross-chain messaging system, identified several areas of concern. The contract leverages OpenZeppelin's upgradeable patterns and implements a burn/mint mechanism for cross-chain transfers. Key findings include significant centralized control by the owner over critical bridge parameters and an operational risk related to the initial token supply distribution.

> **Final Recommendation:** It is strongly recommended to implement a robust multi-signature wallet or a time-locked governance mechanism for the `owner` role to mitigate the high centralization risk, especially for functions that control the `interchainSecurityModule` and `hook` addresses. Additionally, ensure that the address calling the `initialize` function is a secure, intended recipient for the initial token supply to prevent operational errors. All external dependencies, particularly the `interchainSecurityModule` and any configured `hook` contracts, must undergo thorough security audits.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The HypERC20 contract utilizes OpenZeppelin's upgradeable ERC20 and Ownable patterns, demonstrating good adherence to established standards (7.2 Code Security). The cross-chain logic is built upon… |
| **Governance / Economics** | 1/10 | High | The economic model revolves around a standard ERC20 token with a burn/mint mechanism for cross-chain transfers, which is a common and understood pattern (7.4 Economic). However, the governance model… |
| **Upgrades** | 3/10 | High | The contract is designed for upgradeability using the TransparentUpgradeableProxy pattern and OpenZeppelin's upgradeable contracts (7.7 Upgrades). The inclusion of `__GAP` storage slots in parent… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Transparent |
| **Admin** | OZ ProxyAdmin → RoleGatedExecutor |
| **Implementation** | ✅ Verified source |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 92.3% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 2 High · 🟡 2 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `H-01` — Centralized Control over Critical Bridge Parameters  *(Severity: High · Status: Unresolved)*

The `owner` (set via `_MailboxClient_initialize`) has sole control over critical bridge configuration functions such as `setHook`, `setInterchainSecurityModule`, `setDestinationGas`, `enrollRemoteRouter`, and `unenrollRemoteRouter`. These functions directly impact the security and functionality of the cross-chain bridge. A compromise of the owner's private key or a malicious owner could lead to severe consequences, including routing messages through an insecure Interchain Security Module (ISM), setting a malicious hook, or disabling cross-chain transfers.

**Recommendation:** Implement a robust multi-signature wallet or a time-locked governance mechanism for the `owner` role, especially for critical functions like `setInterchainSecurityModule` and `setHook`. This decentralizes control and adds a layer of security against single points of failure.


### `H-02` — Initial Token Supply Mints to `initialize` Caller  *(Severity: High · Status: Unresolved)*

The `initialize` function mints the entire `_totalSupply` to `msg.sender`. In a proxy deployment, `msg.sender` will be the address that calls `initialize` on the proxy, typically the deployer or a `ProxyAdmin` contract. If this address is not the intended final recipient (e.g., a treasury multisig), the tokens must be manually transferred, introducing an operational risk of misdirection or loss.

**Recommendation:** Ensure the address calling `initialize` is a secure, intended recipient (e.g., a multisig wallet) or modify the `initialize` function to accept an explicit `_initialSupplyRecipient` address to which the initial supply should be minted.


### `M-01` — Reliance on External Interchain Security Module (ISM)  *(Severity: Medium · Status: Unresolved)*

The contract's cross-chain security heavily relies on the `_interchainSecurityModule` for message verification. The `setInterchainSecurityModule` function allows the owner to change this critical component. If the configured ISM is vulnerable, malicious, or misconfigured, the integrity of cross-chain messages and the security of the bridged tokens could be compromised.

**Recommendation:** Thoroughly audit and continuously monitor the configured `interchainSecurityModule`. Implement a robust change management process for updating the ISM, ideally involving a time-lock or governance vote to prevent immediate malicious changes.


### `M-02` — Potential for Malicious Hook Configuration  *(Severity: Medium · Status: Unresolved)*

The `setHook` function allows the owner to set an `IPostDispatchHook` contract. While the `onlyContractOrNull` modifier prevents setting an Externally Owned Account (EOA), a malicious or vulnerable hook contract could potentially intercept or manipulate cross-chain messages, or execute unintended logic after dispatch, leading to security or economic issues.

**Recommendation:** Ensure any configured `hook` contract is thoroughly audited and its functionality is well-understood. Consider implementing a whitelist for approved hook contracts or a time-lock for changes to the hook address.


### `L-01` — Multiple Pragma Directives  *(Severity: Low · Status: Unresolved)*

The codebase uses different `pragma solidity` versions across its files (e.g., `>=0.8.0` and `>=0.6.11`). While the main `HypERC20` contract uses `0.8.0`, having mixed pragmas can sometimes lead to compilation issues or subtle behavior differences if not handled carefully by the build system.

**Recommendation:** Standardize all `pragma solidity` directives to a single, consistent version (e.g., `0.8.22` as per compiler version) across the entire codebase to avoid potential inconsistencies and simplify compilation.


### `I-01` — Redundant `OwnershipTransferred` Event Emission  *(Severity: Informational · Status: Unresolved)*

The `_MailboxClient_initialize` function first calls `__Ownable_init()`, which transfers ownership to `msg.sender` and emits an `OwnershipTransferred` event. Subsequently, it calls `_transferOwnership(_owner)`, which transfers ownership again to the specified `_owner` and emits another `OwnershipTransferred` event. While functionally correct, this results in two `OwnershipTransferred` events being emitted during initialization, which could be confusing for event listeners.

**Recommendation:** Consider if the initial `_transferOwnership(msg.sender)` within `__Ownable_init()` is strictly necessary when `_MailboxClient_initialize` immediately overrides it. A common pattern is to initialize `Ownable` with the final `_owner` directly to avoid redundant event emissions.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x8e1e...caef`](https://bscscan.com/address/0x8e1e6bf7e13c400269987b65ab2b5724b016caef) |
| **Network** | BNB Chain |
| **Price** | $0.01723 |
| **24h Volume** | $181.4K |
| **Liquidity** | $72.1K |
| **Volume / Liquidity** | 2.5× |
| **Token Age** | 1y |
| **Top-10 Holders** | 92.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2413 buys / 2817 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xdaf84e35ca400d7641456e53b6a8a30cccecfd5b)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/mito-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-02*
