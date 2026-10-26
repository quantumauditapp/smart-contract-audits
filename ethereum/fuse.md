---
token: Fuse
ticker: FUSE
network: ethereum
risk_score: 6
status: low
date: 2026-09-12
---

# Fuse (FUSE) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 6/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/fuse-eth)

---

## Audit Summary

The audit reviewed the `PairPadLauncherToken` and `PairPadLaunchDeployer` contracts. The system provides a mechanism for deploying ERC20 tokens with an optional, short-duration launch guard. The code leverages OpenZeppelin standards and implements robust access controls for deployment and guard list initialization. Key strengths include immutable contract parameters and metadata length enforcement. However, a critical dependency on the `factory` contract for guard configuration introduces a significant trust assumption, and the centralized control over guard list initialization by the `PairPadLaunchDeployer` is noted. Potential gas issues with very large guard lists and the very short guard window are also identified.

> **Final Recommendation:** It is crucial to thoroughly audit and secure the `factory` contract that implements the `IGuardConfig` interface, as its integrity directly impacts the security of all deployed `PairPadLauncherToken` instances. Consider implementing a mechanism for the `originalDeployer` to review or approve the guard list before it is initialized by the `PairPadLaunchDeployer`, if direct control is desired. Additionally, evaluate the practical implications of the 60-second guard window and the potential for gas limit issues with extremely large guard lists, although the latter is a low probability given typical list sizes.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The technical architecture (7.1) is straightforward, utilizing a factory pattern for token deployment. Code security (7.2) is generally good, with OpenZeppelin standards for ERC20 and ERC20Burnable… |
| **Governance / Economics** | 6/10 | Medium | The economic model (7.4) centers on a standard ERC20 token with a temporary launch guard. The guard's maximum duration is 60 seconds, limiting its long-term impact on token economics. Governance… |
| **Upgrades** | 9/10 | Low | The contracts are not designed to be upgradeable (7.7), as no proxy patterns or upgrade mechanisms are implemented. This eliminates upgrade-related risks but means any future changes would require a… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 2 Medium · 🟢 2 Low · ⚪ 2 Informational_

### `M-01` — Centralized Control over Guard List Initialization  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `creator` of `PairPadLauncherToken` is the `PairPadLaunchDeployer` contract itself, not the `originalDeployer` who initiated the token creation. Consequently, only the `PairPadLaunchDeployer` can call `initGuardList` on the newly deployed token. This means the `originalDeployer` has no direct control over the initialization of the guard list; it is entirely dictated by the `PairPadLaunchDeployer` based on the configuration fetched from `IGuardConfig(factory)`. This centralizes a critical initial setup step (7.3 Access Control, 7.5 Governance).

**Recommendation:** If the `originalDeployer` is intended to have more direct control or oversight, consider modifying the design to allow them to propose or approve the guard list before `PairPadLaunchDeployer` initializes it. Alternatively, clearly communicate this centralized control to all users and `originalDeployer`s.


### `M-02` — Critical Dependency on `IGuardConfig` Implementation  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `PairPadLaunchDeployer` contract critically relies on the `IGuardConfig` interface, specifically `guardSecondsOf` and `guardListOf`, which are called on the `factory` address. The security and integrity of the token's launch guard mechanism (duration and allowed list) are entirely dependent on the correct and non-malicious implementation of these functions within the `factory` contract. A compromised or malicious `factory` could provide incorrect guard configurations, potentially allowing unauthorized transfers during the guard period or disabling the guard entirely. This introduces a significant trust assumption o

**Recommendation:** Ensure the `factory` contract implementing `IGuardConfig` is thoroughly audited, highly secure, and its access controls are robust. Consider adding safeguards or multi-signature approvals for changes to the `factory`'s guard configuration logic. Document this critical dependency clearly for users and `originalDeployer`s.


### `L-01` — Potential Gas Limit Issues for `initGuardList` with Large Lists  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `initGuardList` function iterates through an array of addresses provided by `IGuardConfig(factory).guardListOf`. If this array contains an extremely large number of addresses, the transaction to initialize the guard list could exceed the block gas limit, causing the transaction to revert. This would prevent the guard list from being fully set, potentially leaving the token in an unexpected state regarding its transfer restrictions (7.2 Code Security, 7.8 Operations).

**Recommendation:** Implement a maximum practical limit on the size of the `list` array that can be passed to `initGuardList` within the `IGuardConfig` implementation or `PairPadLaunchDeployer`. Alternatively, consider a batched approach for adding allowed addresses if very large lists are anticipated, though this would require design changes to `initGuardList`.


### `L-02` — Metadata String Length Limits Only Enforced at Deployment  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `PairPadLaunchDeployer` contract enforces `MAX_NAME_LENGTH`, `MAX_SYMBOL_LENGTH`, etc., for metadata fields during the `deployToken` function. While this prevents excessively long strings from being stored during initial deployment, the `PairPadLauncherToken` itself does not have any setter functions for these metadata fields. If the design were to change to allow updates, the lack of length checks within the token contract itself could become an issue. Given the current immutable design, this is a minor observation (7.2 Code Security).

**Recommendation:** No action required for the current design. If future upgrades introduce mutable metadata fields, ensure that appropriate length validation is implemented within the setter functions in the `PairPadLauncherToken` contract.


### `I-01` — Short Guard Window Duration  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `MAX_GUARD_SECONDS` constant is set to 60 seconds. This means the 'launch guard' mechanism, which restricts transfers for non-allowed recipients, is active for a very short period. While this might be intentional for rapid token launches, it significantly limits the practical utility of the guard for preventing sustained bot activity or large-scale dumping beyond the immediate launch minute (7.4 Economic).

**Recommendation:** Confirm that a 60-second guard window aligns with the intended security and economic strategy for token launches. If longer protection is desired, the `MAX_GUARD_SECONDS` constant would need to be increased, along with a re-evaluation of its implications.


### `I-02` — `owner()` Function Returns `address(0)`  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `owner()` function, commonly found in OpenZeppelin's `Ownable` contracts or similar access control patterns, is explicitly overridden in `PairPadLauncherToken` to always return `address(0)`. This indicates a deliberate design choice for the token to have no single administrative owner after deployment, relying on the `creator` (PairPadLaunchDeployer) for `initGuardList` and the immutability of other parameters (7.3 Access Control).

**Recommendation:** No action required, as this appears to be an intentional design decision. Ensure this characteristic is clearly documented for users and developers to avoid confusion regarding token ownership and administrative capabilities.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x126f...1111`](https://etherscan.io/address/0x126f5ece91d971f8ad62fa4fc1054456b8bd1111) |
| **Network** | Ethereum |
| **Price** | $0.0005812 |
| **24h Volume** | $574.9K |
| **Liquidity** | $96.1K |
| **Volume / Liquidity** | 6.0× |
| **Token Age** | 1d |
| **Top-10 Holders** | 23.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1019 buys / 773 sells |

## Security Flags (4/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0x90a64ed1c47392829a39df15ff25401c21818ea2db9e2538c9c25182f76b7c1e)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/fuse-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-12*
