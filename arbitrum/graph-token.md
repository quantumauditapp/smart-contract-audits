---
token: Graph Token
ticker: GRT
network: arbitrum
risk_score: 63
status: medium
date: 2026-09-06
---

# Graph Token (GRT) — Smart Contract Security Analysis | Arbitrum

> **Risk Score: 63/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/graph-token-arb)

---

## Audit Summary

The L2GraphToken contract, serving as an upgradeable ERC-20 token on Arbitrum, exhibits a critical flaw in its initialization mechanism, preventing it from being properly set up after deployment or upgrade. This issue, combined with significant centralization risks associated with the governor role, elevates the overall risk level to High. While the contract incorporates standard ERC-20 features, OpenZeppelin upgradeable patterns, and a two-step ownership transfer, the uncallable `initialize` function and the broad powers of the governor require immediate attention. Additional concerns include front-running susceptibility in the `permit` function and misleading custom upgrade logic.

> **Final Recommendation:** Address the critical `initialize` function flaw by removing or correcting the `onlyImpl` modifier to allow proper contract initialization via the proxy. Re-evaluate the `_implementation()` logic in `GraphUpgradeable` to ensure it aligns with standard proxy patterns or is clearly documented for its custom behavior. Implement robust multi-signature control for the `governor` role to mitigate centralization risks and consider time-locks for critical administrative actions. Additionally, review the `permit` function for potential front-running mitigations to improve user experience and prevent transaction failures.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 3/10 | High | The contract leverages OpenZeppelin's upgradeable ERC-20 standards, including `ERC20BurnableUpgradeable` and EIP-2612 `permit` functionality, enhancing token utility and security. It employs clear… |
| **Governance / Economics** | 1/10 | High | The contract implements a two-step ownership transfer mechanism, requiring a `pendingGovernor` to accept ownership, which is a good practice for mitigating immediate risks of accidental transfers… |
| **Upgrades** | 1/10 | High | The contract is designed to be upgradeable, utilizing OpenZeppelin's `Upgradeable` pattern with a `__gap` storage variable to ensure future compatibility (7.7 Upgrades). It includes custom… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Transparent |
| **Admin** | ⚠️ EOA (single key controls upgrades) |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | 10.6% |
| **Top-3 Unlocked** | 28.1% |

## Security Findings

_🔴 1 Critical · 🟠 2 High · 🟡 1 Medium · 🟢 2 Low_

### `C-01` — Critical: `initialize` function cannot be called via proxy due to `onlyImpl` modifier  *(Severity: Critical · Status: Unresolved)*

The `initialize` function in `L2GraphToken` is marked with `external onlyImpl initializer`. The `onlyImpl` modifier requires `msg.sender == _implementation()`. The `_implementation()` function reads the `IMPLEMENTATION_SLOT` from the *current contract's storage*. For an implementation contract (like `L2GraphToken` itself), this slot is typically empty (0), meaning `_implementation()` would return `address(0)`. Consequently, `onlyImpl` would require `msg.sender == address(0)`, which is impossible for any transaction. This prevents the `initialize` function from ever being called through the proxy, leaving the contract uninitialized. An uninitialized contract would have its `governor`, `gatew…

**Recommendation:** Remove the `onlyImpl` modifier from the `initialize` function. The `initializer` modifier from OpenZeppelin is sufficient to ensure it's called only once. If `onlyImpl` was intended for a specific custom proxy interaction, this logic must be thoroughly re-evaluated and corrected to allow proxy-based initialization.


### `H-01` — High: Centralization Risk with Governor Role  *(Severity: High · Status: Unresolved)*

The `governor` role holds extensive control over critical contract functionalities. The `governor` can set the `gateway` (which controls `bridgeMint` and `bridgeBurn`), set the `l1Address`, and add/remove `minters` (who can `mint` new tokens). If the `governor`'s private key is compromised, it could lead to unauthorized minting, burning, and manipulation of bridge operations, posing a significant centralization risk (7.3 Access Control, 7.4 Economic). While a two-step ownership transfer exists, the power remains concentrated in a single entity (or multisig).

**Recommendation:** Implement a robust multi-signature wallet (e.g., Gnosis Safe) for the `governor` address to distribute control and reduce the risk of a single point of failure. Consider implementing time-locks for highly sensitive actions (e.g., `setGateway`, `addMinter`) to provide a window for intervention if a malicious transaction is initiated.


### `H-02` — High: `permit` function susceptible to front-running for transaction failure  *(Severity: High · Status: Unresolved)*

The EIP-2612 `permit` function allows users to approve token transfers off-chain. While the `nonce` mechanism prevents replay attacks, the function is susceptible to front-running. A malicious actor could observe a pending `permit` transaction and submit their own transaction with a higher gas price, causing the legitimate user's transaction to fail due to the `nonce` being incremented by the front-running transaction. Although this does not lead to direct fund loss for the `_owner`, it results in wasted gas and a poor user experience (7.2 Code Security).

**Recommendation:** While inherent to the `permit` design, users should be aware of this behavior. Consider implementing a mechanism where the `permit` signature includes a `minGasPrice` or similar parameter, or advise users to use a transaction relayer that can handle such scenarios gracefully. Ensure clear documentation for users regarding potential transaction failures.


### `M-01` — Medium: Misleading `_implementation()` logic in `GraphUpgradeable`  *(Severity: Medium · Status: Unresolved)*

The `_implementation()` function in `GraphUpgradeable` reads the `IMPLEMENTATION_SLOT` from the *current contract's storage*. For an implementation contract, this slot is not used to store its own address or the proxy's implementation address; it's the proxy that stores the implementation address in this slot. This function will likely return `address(0)` or an incorrect address when called on the implementation contract, making it unsuitable for determining the actual implementation address in a standard EIP-1967 proxy context. This misleading logic contributes to the critical `initialize` issue (C-01) and can cause confusion or unexpected behavior in custom upgrade mechanisms (7.1 Archite…

**Recommendation:** Refactor `_implementation()` to correctly retrieve the proxy's implementation address if it's intended to be used by the implementation contract to query its proxy. Alternatively, remove this function if its current implementation is not serving a valid purpose within the upgrade pattern, and ensure any modifiers relying on it (like `onlyImpl`) are corrected.


### `L-01` — Low: Hardcoded `DOMAIN_SALT`  *(Severity: Low · Status: Unresolved)*

The `DOMAIN_SALT` used in the EIP-712 `DOMAIN_SEPARATOR` calculation is a hardcoded `bytes32` value. While not a direct vulnerability, hardcoding this value can limit flexibility if the contract were to be deployed in multiple environments or chains where a unique salt might be desired to prevent potential domain collisions or improve clarity (7.2 Code Security).

**Recommendation:** Consider making the `DOMAIN_SALT` configurable during initialization or deriving it from a unique, immutable contract parameter (e.g., `block.chainid` combined with a deployment-specific value) to enhance flexibility and ensure uniqueness across different deployments or networks.


### `L-02` — Low: `_initialSupply` in `_initialize` is always zero for L2GraphToken  *(Severity: Low · Status: Unresolved)*

The `GraphTokenUpgradeable._initialize` function accepts an `_initialSupply` parameter to mint tokens to the owner upon initialization. However, the `L2GraphToken.initialize` function explicitly calls `GraphTokenUpgradeable._initialize(_owner, 0);`, always passing `0` for the initial supply. This means no tokens are minted to the owner during the contract's initialization, making the `_initialSupply` parameter in the base `_initialize` function effectively unused by this concrete implementation. While this might be intentional for a bridge token where supply is managed via bridging, it could be misleading or an oversight if initial supply was expected (7.8 Operations).

**Recommendation:** Confirm if the intention is indeed to start with zero initial supply and manage all token issuance via the bridge. If so, consider removing the `_initialSupply` parameter from `GraphTokenUpgradeable._initialize` or clearly documenting its intended use for other implementations. If an initial supply is desired, adjust the `L2GraphToken.initialize` call accordingly.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x9623...88c7`](https://arbiscan.io/address/0x9623063377ad1b27544c965ccd7342f7ea7e88c7) |
| **Network** | Arbitrum |
| **Price** | $0.02055 |
| **24h Volume** | $37.1K |
| **Liquidity** | $67.1K |
| **Volume / Liquidity** | 0.6× |
| **Token Age** | 3y |
| **Top-10 Holders** | 87.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 454 buys / 317 sells |

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

- [View on DexScreener](https://dexscreener.com/arbitrum/0x74d0ae8b8e1fca6039707564704a25ad2ee036b0)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/graph-token-arb)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-06*
