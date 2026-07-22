---
token: Arcium
ticker: ARX
network: bsc
risk_score: 100
status: critical
date: 2026-07-22
---

# Arcium (ARX) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 100/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/arcium-bsc)

---

## Audit Summary

The PeerToken contract implements an ERC20 token with minting and burning capabilities, utilizing OpenZeppelin's Ownable and ERC20Burnable. However, a critical dependency on an unaudited `BaseToken` contract for core transfer logic, coupled with a direct override of `_update` to call `BaseToken._update` instead of `super._update`, introduces significant unknown risks. The contract also exhibits high centralization risk due to the owner's ability to control the minter, who can mint an unlimited supply of tokens.

> **Final Recommendation:** It is imperative to provide the full source code for the `BaseToken` contract to allow for a comprehensive security review of the token's core transfer logic. The `_update` function's delegation to `BaseToken._update` should be thoroughly reviewed to ensure it correctly implements or delegates to the standard ERC20 transfer mechanisms, or `super._update` should be called. Consider implementing a multi-signature wallet for the `owner` and `minter` roles to mitigate centralization risks and enhance operational security.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 1/10 | High | The contract leverages OpenZeppelin libraries for ERC20 and Ownable functionalities, which is a good practice for code security (7.2). Custom error messages are also implemented, enhancing user… |
| **Governance / Economics** | 1/10 | High | The contract implements a two-tiered access control system with an `owner` and a `minter` (7.3). The `owner` has the power to set the `minter`, and the `minter` can mint an arbitrary amount of tokens… |
| **Upgrades** | 3/10 | High | The PeerToken contract is not designed with upgradeability features (7.7). This means its logic is immutable once deployed, eliminating risks associated with proxy patterns or upgrade mechanisms. Any… |

## Security Findings

_🔴 2 Critical · 🟠 1 High · 🟡 1 Medium · ⚪ 2 Informational_

### `C-01` — Unauditable Core Logic Due to Missing `BaseToken` Source  *(Severity: Critical · Status: Unresolved)*

The `PeerToken` contract inherits from `BaseToken` and explicitly delegates its core `_update` function (responsible for all token transfers, mints, and burns) to `BaseToken._update`. Without the source code for `BaseToken.sol`, it is impossible to audit the fundamental mechanics of token transfers, balance updates, and total supply management. This introduces an unknown and potentially severe vulnerability, as `BaseToken` could contain critical flaws (e.g., incorrect balance updates, reentrancy vectors, or improper handling of zero addresses) that would directly impact `PeerToken`'s integrity (7.1 Architecture, 7.2 Code Security).

**Recommendation:** Provide the complete and verified source code for `src/BaseToken.sol`. A full audit of `BaseToken` is required to ensure the security and correctness of `PeerToken`'s core functionality. Until `BaseToken` is audited, the security of `PeerToken` cannot be guaranteed.


### `C-02` — Critical `_update` Override Bypassing ERC20 Standard Logic  *(Severity: Critical · Status: Unresolved)*

The `PeerToken` contract overrides the `_update` function, which is a critical internal function in OpenZeppelin's ERC20 implementation responsible for handling all token movements. Instead of calling `super._update()` to ensure the standard ERC20 logic (e.g., balance checks, total supply updates, event emissions) is executed, `PeerToken` directly calls `return BaseToken._update(_from, _to, _value);`. This design choice means that `PeerToken`'s core transfer logic is entirely dependent on `BaseToken`'s implementation, potentially bypassing or incorrectly implementing crucial ERC20 safeguards provided by OpenZeppelin's `ERC20` contract. If `BaseToken._update` does not correctly replicate or…

**Recommendation:** Review the `_update` override in `PeerToken` and the implementation of `BaseToken._update`. Ensure that `BaseToken._update` correctly implements all necessary ERC20 transfer logic, including balance updates, total supply adjustments, and zero-address checks, or that it properly calls `super._update()` if `BaseToken` also inherits from `ERC20`. A safer approach in `PeerToken` might be to call `super._update()` directly if `BaseToken` is intended to be a simple extension, or to ensure `BaseToken`…


### `H-01` — Centralized Minting Authority and Unlimited Supply Risk  *(Severity: High · Status: Unresolved)*

The contract design grants significant power to the `minter` role, allowing them to mint an arbitrary amount of tokens via the `mint` function. Furthermore, the `owner` (a single external address) has the exclusive ability to change the `minter` at any time via `setMinter`. This creates a high centralization risk (7.4 Economic, 7.5 Governance). If the `owner` address or the `minter` address is compromised, an attacker could mint an unlimited supply of tokens, leading to hyperinflation and a complete loss of value for existing token holders. This also presents a single point of failure for the token's economic stability (7.8 Operations).

**Recommendation:** Consider implementing a multi-signature wallet for both the `owner` and `minter` roles to distribute control and reduce the risk of a single point of failure. Explore mechanisms to cap the total supply or introduce rate limits for minting to prevent uncontrolled inflation. If unlimited minting is a core design choice, ensure robust operational security for the `minter` and `owner` keys.


### `M-01` — Lack of Role Renouncement or Multi-sig Integration  *(Severity: Medium · Status: Unresolved)*

The `Ownable` pattern is used, but there is no explicit function to renounce ownership or transfer it to a zero address, which could be a desired feature for decentralization or to prevent accidental control. Similarly, there is no mechanism to renounce the `minter` role. While `setMinter` allows changing the minter, it does not prevent setting it to a malicious address or a non-existent one if not handled carefully (though `InvalidMinterZeroAddress` prevents setting to `address(0)`). The absence of multi-signature wallet integration for these critical roles increases operational risk (7.3 Access Control, 7.8 Operations).

**Recommendation:** Consider adding a `renounceOwnership()` function to allow the owner to permanently give up control, if desired for future decentralization. Implement a similar `renounceMinter()` function. For enhanced security, integrate a multi-signature wallet solution for the `owner` and `minter` roles from the outset to ensure critical operations require consensus from multiple trusted parties.


### `I-01` — Use of Custom Errors  *(Severity: Informational · Status: Unresolved)*

The contract utilizes custom errors (`CallerNotMinter`, `InvalidMinterZeroAddress`) instead of traditional `require()` statements with string messages. This is a good practice in Solidity as custom errors are more gas-efficient and provide clearer, structured error information to off-chain applications (7.2 Code Security).

**Recommendation:** Continue using custom errors for all revert conditions throughout the codebase. This enhances gas efficiency and improves the developer experience for integrators.


### `I-02` — Explicit `_update` Override for Clarity  *(Severity: Informational · Status: Unresolved)*

The `_update` function is explicitly declared with `override(ERC20, BaseToken)`, clearly indicating that it overrides implementations from both parent contracts. This improves code readability and helps prevent potential issues in complex inheritance hierarchies (7.1 Architecture, 7.2 Code Security).

**Recommendation:** Maintain explicit `override` declarations for all functions that override multiple parent implementations. This practice contributes to clearer code structure and maintainability.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xd5f6...a715`](https://bscscan.com/address/0xd5f6ef5deabe61e6d5cdb49bfb6f156f2c1ca715) |
| **Network** | BNB Chain |
| **Price** | $0.1662 |
| **24h Volume** | $51.4K |
| **Liquidity** | $23.1K |
| **Volume / Liquidity** | 2.2× |
| **Token Age** | 1mo |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 680 buys / 579 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ❌ Fail |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ❌ | Source code is **not verified** — contract logic is opaque. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x56336db9642763b34b746cf38ca2e7657f243a43)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/arcium-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-07-22*
