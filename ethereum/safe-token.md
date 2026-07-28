---
token: Safe Token
ticker: SAFE
network: ethereum
risk_score: 47
status: high
date: 2026-07-27
---

# Safe Token (SAFE) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 47/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/safe-token-eth)

---

## Audit Summary

The SafeToken contract is an ERC20 token with Pausable and Ownable functionalities, inheriting from OpenZeppelin standards. It includes a TokenRescuer mechanism. The contract is not upgradeable. The primary risks identified relate to the significant centralized control held by the contract owner over token operations and supply, although the owner is a multisig.

> **Final Recommendation:** It is recommended to thoroughly review the operational procedures for the owner's multisig, ensuring robust key management and clear decision-making processes given the extensive control over token operations. Consider implementing a time-lock for critical owner actions, such as unpausing or transferring ownership, to provide a window for community review and reaction. For future iterations, evaluate the trade-offs between immutability and upgradeability, and if flexibility is desired, explore proxy patterns.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The technical architecture is straightforward, leveraging battle-tested OpenZeppelin contracts for ERC20, Ownable, and Pausable functionalities (7.1 Architecture). The code quality is high, with… |
| **Governance / Economics** | 3/10 | High | The contract exhibits a high degree of centralized control, with the owner possessing the ability to pause/unpause transfers, bypass pause restrictions for their own transfers, and rescue any ERC20… |
| **Upgrades** | 7/10 | Low | The `SafeToken` contract is deployed as a non-upgradeable implementation (7.7 Upgrades). This design choice provides immutability, ensuring the contract's logic remains constant post-deployment.… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 88.9% |
| **Top-3 Unlocked** | ⚠️ 92.3% |

## Security Findings

_🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 2 Informational_

### `H-01` — Significant Centralized Control by Owner  *(Severity: High · Status: Unresolved)*

The `Ownable` pattern grants extensive power to a single address (or multisig) designated as the owner. The owner can pause/unpause all token transfers, bypass the pause mechanism for their own transfers, and rescue any ERC20 tokens accidentally sent to the contract. While the owner is a multisig, which mitigates a single point of failure, this still represents a highly centralized control point. A compromise of the multisig or malicious actions by its signers could lead to severe consequences, including freezing user funds or unauthorized token movements.

**Recommendation:** Implement a time-lock mechanism for critical owner-controlled functions (e.g., `unpause`, `transferOwnership`, `rescueToken`). This would introduce a delay before actions take effect, allowing for community oversight and potential intervention. Additionally, consider exploring decentralized governance models for future iterations to distribute control and reduce reliance on a single entity.


### `M-01` — Owner Can Bypass Pause for Transfers  *(Severity: Medium · Status: Unresolved)*

The `_beforeTokenTransfer` function includes a condition `owner() == _msgSender()` which allows the contract owner to perform token transfers even when the contract is in a paused state. While this might be an intended emergency feature, it means the owner is not subject to the same restrictions as other users during a pause. This could lead to perceived unfairness, potential market manipulation, or allow the owner to move tokens while other users are restricted.

**Recommendation:** Clearly document the intended use cases and operational procedures for the owner's ability to bypass the pause. If this functionality is not strictly necessary for emergency operations, consider removing the `owner() == _msgSender()` condition from the `_beforeTokenTransfer` function to ensure all users, including the owner, are subject to the same pause restrictions. If kept, ensure robust internal controls for the multisig are in place to prevent misuse.


### `L-01` — Initial Large Token Mint to Owner  *(Severity: Low · Status: Unresolved)*

The contract's constructor mints 1,000,000,000 tokens (with 18 decimals) directly to the deployer/owner address. This means 100% of the initial token supply is held by a single entity. While this is a common pattern for initial token deployments, it grants immense control over the token's initial distribution, liquidity, and potential market impact to the owner. Any subsequent distribution relies entirely on the owner's actions.

**Recommendation:** Ensure that the distribution plan for these tokens is transparent and clearly communicated to the community. Consider vesting schedules or multi-signature controlled distribution mechanisms to manage the release of these tokens over time, reducing the immediate concentration of power and potential for market shocks.


### `I-01` — Non-Upgradeable Contract Design  *(Severity: Informational · Status: Unresolved)*

The `SafeToken` contract is deployed as a standard implementation contract and does not utilize any proxy patterns (e.g., UUPS, Transparent). This design choice means the contract's logic cannot be modified or upgraded after deployment. While this provides immutability and reduces complexity associated with upgrade mechanisms, it also implies that any bugs discovered post-deployment cannot be fixed, and new features cannot be added without a complete redeployment and user migration, which can be a costly and disruptive process.

**Recommendation:** Acknowledge the implications of non-upgradeability. If future flexibility for bug fixes or feature enhancements is desired, consider implementing an upgradeable proxy pattern in future contract deployments. If immutability is the explicit goal, ensure thorough testing and auditing are conducted pre-deployment to minimize the risk of unfixable issues.


### `I-02` — Redundant Pause Check in `unpause()`  *(Severity: Informational · Status: Unresolved)*

The `unpause()` function explicitly includes `require(paused(), "SafeToken: token is not paused");`. However, the internal `_unpause()` function, which `unpause()` calls, is already protected by the `whenPaused` modifier. This modifier performs the exact same check, making the explicit `require` statement in `unpause()` redundant.

**Recommendation:** Remove the redundant `require(paused(), "SafeToken: token is not paused");` statement from the `unpause()` function. The `whenPaused` modifier on `_unpause()` already ensures the contract is paused before attempting to unpause, simplifying the code without affecting functionality.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x5afe...eeee`](https://etherscan.io/address/0x5afe3855358e112b5647b952709e6165e1c1eeee) |
| **Network** | Ethereum |
| **Price** | $0.09032 |
| **24h Volume** | $655.3K |
| **Liquidity** | $191.1K |
| **Volume / Liquidity** | 3.4× |
| **Token Age** | 2y |
| **Top-10 Holders** | 79.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 910 buys / 1036 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Frequently Asked Questions

### Is Safe Token a scam?

Based on automated analysis, Safe Token scores 63/100 (High Risk) on our risk scale. No honeypot was detected, but always verify independently before investing.

### Is Safe Token safe to buy?

Our scanner flagged a risk score of 63/100. Ownership has not been renounced, which is a risk factor. DYOR before purchasing any token.

### Has Safe Token been audited?

The contract has not been verified on-chain. Verification is not the same as a full security audit. Use Quantum Audit's free tool to run a deeper analysis of the contract code.

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0x000ba527862e5b82cff0f7c66b646af023274aa1)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/safe-token-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-07-27*
