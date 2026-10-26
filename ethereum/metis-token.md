---
token: Metis Token
ticker: METIS
network: ethereum
risk_score: 37
status: medium
date: 2026-09-28
---

# Metis Token (METIS) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 37/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/metis-token-eth)

---

## Audit Summary

This audit covers the ERC20 token contract, which appears to be a standard OpenZeppelin implementation. The contract utilizes SafeMath for arithmetic safety and adheres to the ERC20 standard. It is not upgradeable, and ownership has been renounced, contributing to decentralization. The primary risks identified are minor and informational, related to the use of an older Solidity version and the inherent front-running vulnerability in the ERC20 `approve` function, which is mitigated by alternative functions.

> **Final Recommendation:** It is recommended to review the implementation of the derived `MToken` contract, specifically how `_mint` and `_burn` functions are controlled, to ensure the overall economic model aligns with expectations. While the `approve` front-running vulnerability is inherent to ERC20, users should be encouraged to use `increaseAllowance` and `decreaseAllowance` where possible. For future developments, consider using a more recent Solidity compiler version to benefit from newer language features and optimizations.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The technical architecture (7.1 Architecture) is robust, leveraging well-audited OpenZeppelin ERC20 and SafeMath libraries. Code security (7.2 Code Security) is strong, with SafeMath preventing… |
| **Governance / Economics** | 6/10 | Medium | The economic model (7.4 Economic) of the base ERC20 contract is sound, relying on a derived contract (MToken) for supply mechanisms like minting and burning. The prefill indicates… |
| **Upgrades** | 6/10 | Medium | The contract is not designed to be upgradeable (7.7 Upgrades), as indicated by `is_proxy: false`. This eliminates upgrade-related risks such as proxy storage collisions or faulty implementation… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟢 1 Low · ⚪ 3 Informational_

### `L-01` — ERC20 `approve` Function Front-Running Vulnerability  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The standard ERC20 `approve` function is susceptible to a front-running attack. If a user approves an amount for a spender, and then decides to change that approved amount, a malicious actor could front-run the second `approve` transaction. This allows the attacker to spend the original allowance before the new allowance is set, and then spend the new allowance, effectively spending more than intended by the user. The contract includes `increaseAllowance` and `decreaseAllowance` as mitigations.

**Recommendation:** Advise users to exclusively use `increaseAllowance` and `decreaseAllowance` instead of directly calling `approve` when modifying an existing allowance. Educate users on the risks associated with the direct `approve` function.


### `I-01` — Use of Older Solidity Compiler Version  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract is compiled with Solidity version `^0.5.0` (specifically 0.5.16). While this version is stable, newer Solidity versions (e.g., 0.8.x) offer additional security features, gas optimizations, and clearer error handling (e.g., default checked arithmetic, custom errors).

**Recommendation:** For new deployments or significant upgrades, consider migrating to a more recent Solidity compiler version (e.g., 0.8.x) to leverage improved security features and optimizations. Thorough testing would be required for any migration.


### `I-02` — Non-Upgradeability of Contract  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract is not designed with upgradeability in mind, as indicated by `is_proxy: false`. This means that once deployed, the contract's logic cannot be modified. While this eliminates risks associated with upgrade mechanisms, it also prevents bug fixes, feature additions, or parameter changes without deploying an entirely new contract and migrating assets.

**Recommendation:** Acknowledge the trade-offs of non-upgradeability. For contracts intended to be immutable, this is a desired feature. For projects requiring future flexibility, consider proxy patterns (e.g., UUPS, Transparent) in future contract designs.


### `I-03` — Reliance on Derived Contract for Supply Mechanism  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The provided `ERC20.sol` contract serves as a base implementation and does not define the token's supply mechanism (minting/burning). These functionalities are expected to be implemented in a derived contract, such as `MToken`, using the internal `_mint` and `_burn` functions. The security and economic stability of the token heavily depend on the access control and logic within the derived contract's supply functions.

**Recommendation:** Ensure that the derived `MToken` contract implements robust access control for `_mint` and `_burn` functions, restricting them to authorized entities or predefined conditions. A separate audit of the `MToken` contract's specific implementation is crucial.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x9e32...ed8e`](https://etherscan.io/address/0x9e32b13ce7f2e80a01932b42553652e053d6ed8e) |
| **Network** | Ethereum |
| **Price** | $3.5400 |
| **24h Volume** | $94.3K |
| **Liquidity** | $712.0K |
| **Volume / Liquidity** | 0.1× |
| **Token Age** | 5y |
| **Top-10 Holders** | 84.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 183 buys / 170 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0x1c98562a2fab5af19d8fb3291a36ac3c618835d9)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/metis-token-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-28*
