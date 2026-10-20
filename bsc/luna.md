---
token: LUNA
ticker: LUNA
network: bsc
risk_score: 38
status: medium
date: 2026-09-23
---

# LUNA (LUNA) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 38/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/luna-bsc)

---

## Audit Summary

The audit of the BridgeToken implementation contract (TokenImplementation) reveals a critical inability to assess upgrade safety due to the unavailability of the `TokenState` contract source code. This prevents verification of storage layout compatibility, a fundamental requirement for proxy-based systems. The contract otherwise implements standard ERC-20 functionality, including EIP-2612 permit, with appropriate access controls for minting, burning, and metadata updates. Centralized control by the owner for supply management is noted as a medium risk.

> **Final Recommendation:** Prioritize obtaining and auditing the `TokenState` contract to ensure storage layout compatibility and prevent critical vulnerabilities during upgrades. Implement robust security measures for the owner's private key, such as a multi-signature wallet, given the extensive control over token supply and metadata. Consider documenting the known front-running risks associated with the EIP-2612 permit function for users. Review the `Ownable` import and custom owner logic for clarity and to avoid potential future conflicts.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 5/10 | Medium | The contract provides a robust implementation of the ERC-20 standard, including EIP-2612 permit functionality, leveraging OpenZeppelin libraries for cryptographic operations (7.2 Code Security).… |
| **Governance / Economics** | 6/10 | Medium | The token design grants significant centralized control to the `owner` address (7.3 Access Control). The owner can `mint` new tokens, `burn` existing tokens, and `updateDetails` (metadata) (7.4… |
| **Upgrades** | 1/10 | High | The contract is designed as an implementation for a BeaconProxy, indicating an upgradeable architecture (7.7 Upgrades). However, the `TokenState` contract, which defines the storage layout for all… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Beacon |
| **Implementation** | ✅ Verified source |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | 12.0% |
| **Top-3 Unlocked** | 27.5% |

## Security Findings

_🔴 1 Critical · 🟡 1 Medium · 🟢 1 Low · ⚪ 2 Informational_

### `C-01` — Undeterminable Storage Layout for Proxy Upgrades  *(Severity: Critical · Status: Unresolved)*

The `TokenImplementation` contract relies on an external `TokenState` contract for its state variables. Without the source code for `TokenState`, it is impossible to verify the storage layout, which is a critical component for ensuring upgrade safety in a proxy pattern (especially `BeaconProxy`). Incorrect storage layout can lead to storage collisions, data corruption, and severe vulnerabilities upon upgrade. This makes a full audit of the upgrade mechanism impossible.

**Recommendation:** Provide the source code for the `TokenState` contract. A thorough review of its storage layout is essential to confirm compatibility with the proxy pattern and prevent storage collisions during upgrades. Ensure that `TokenState` adheres to proxy-safe storage principles, such as using `ERC1967Storage` or explicitly defining storage slots to avoid conflicts.


### `M-01` — Centralized Control (Owner Privileges)  *(Severity: Medium · Status: Unresolved)*

The `owner` address has significant control over the token supply and metadata. The `mint`, `burn`, and `updateDetails` functions are restricted to `onlyOwner`. While common for bridge tokens, this centralizes trust in a single entity or multisig, posing a medium risk if the owner's private key is compromised or if the owner acts maliciously.

**Recommendation:** Implement a robust access control mechanism for the owner, such as a multi-signature wallet (e.g., Gnosis Safe) or a time-locked governance contract, to mitigate the risk of a single point of failure. Clearly document the owner's responsibilities and the process for any changes to these privileges.


### `L-01` — `permit` Front-Running Vulnerability  *(Severity: Low · Status: Unresolved)*

The EIP-2612 `permit` function is inherently susceptible to front-running attacks. A signed permit message, once broadcast, can be observed by malicious actors who could then submit their own transaction with a higher gas price to front-run the legitimate user's transaction. This could lead to the legitimate user's transaction failing or the approved amount being exploited. This is a known characteristic of `permit` and not a flaw in the implementation itself, but a risk for users.

**Recommendation:** Educate users about the potential for front-running with `permit` transactions. Advise them to use private transaction relays or to be cautious when broadcasting signed messages publicly. This is typically a user-side mitigation rather than a contract-side fix.


### `I-01` — Redundant `Ownable` Import and Custom Owner Logic  *(Severity: Informational · Status: Unresolved)*

The contract imports `Ownable.sol` but then implements its own `owner()` function and `onlyOwner` modifier, relying on `_state.owner`. This creates redundancy and potential for confusion. If `TokenState` also inherits from `Ownable` or defines its own `_owner` variable, it could lead to storage collisions or unexpected behavior. It is generally better to either fully utilize `Ownable`'s functionality or completely omit its import if custom access control is preferred.

**Recommendation:** Choose one approach for ownership: either fully inherit and utilize OpenZeppelin's `Ownable` contract, or remove the `Ownable` import and rely solely on the custom `_state.owner` and associated logic. This improves clarity and reduces potential for storage conflicts.


### `I-02` — Dynamic `_initializePermitStateIfNeeded` Calls  *(Severity: Informational · Status: Unresolved)*

The `_initializePermitStateIfNeeded` function is called within `permit` and `_domainSeparatorV4` if `cachedThis` or `cachedChainId` do not match the current context. While this ensures the EIP-712 domain separator is always up-to-date, it introduces a small, recurring gas overhead on `permit` calls if the cached values are frequently invalidated (e.g., if the contract address or chain ID were to change, which is highly unlikely for a deployed contract).

**Recommendation:** This is a minor efficiency consideration. Given the unlikelihood of `address(this)` or `block.chainid` changing for a deployed contract, the current implementation is acceptable. No immediate action is required, but it's noted for completeness.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x156a...8962`](https://bscscan.com/address/0x156ab3346823b651294766e23e6cf87254d68962) |
| **Network** | BNB Chain |
| **Price** | $0.00006028 |
| **24h Volume** | $75.0K |
| **Liquidity** | $94.4K |
| **Volume / Liquidity** | 0.8× |
| **Token Age** | 4y |
| **Top-10 Holders** | 14.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 766 buys / 838 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x34c422989df98e8369f28eb9799eac1be2df70d0)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/luna-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-23*
