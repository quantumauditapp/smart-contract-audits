---
token: SoSoValue
ticker: SOSO
network: base
risk_score: 53
status: high
date: 2026-08-15
---

# SoSoValue (SOSO) — Smart Contract Security Analysis | Base

> **Risk Score: 53/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/sosovalue-base)

---

## Audit Summary

The OptimismMintableERC20 contract serves as a standard ERC-20 token on an L2 (like Base), designed to be minted and burned exclusively by a designated bridge contract. The contract itself is well-structured, utilizes OpenZeppelin libraries, and implements robust access control for its core functionalities. The primary risk stems from its inherent dependency on the security and integrity of the external bridge contract, which controls the token's supply.

> **Final Recommendation:** Prioritize the security of the `BRIDGE` contract, as it holds ultimate control over the token supply. Ensure the bridge contract undergoes rigorous security audits and maintains robust operational security practices. Consider implementing multi-signature controls or time-locks for critical bridge operations if not already in place. Regularly review the `REMOTE_TOKEN` and `BRIDGE` addresses to confirm their integrity and prevent any unauthorized changes to the L1 token or L2 bridge.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The technical implementation of the OptimismMintableERC20 contract is robust (7.2 Code Security). It leverages battle-tested OpenZeppelin libraries for ERC-20 functionality, minimizing common… |
| **Governance / Economics** | 2/10 | High | The economic security of this token is critically dependent on the external `BRIDGE` contract (7.4 Economic, 7.6 External). The `BRIDGE` address has the sole authority to mint and burn tokens… |
| **Upgrades** | 2/10 | High | The OptimismMintableERC20 contract is not designed to be upgradeable (7.7 Upgrades). It is deployed as a standard implementation contract without proxy patterns. This eliminates upgrade-related risks… |

## Security Findings

_🟡 1 Medium · 🟢 1 Low · ⚪ 2 Informational_

### `M-01` — Critical Dependency on External Bridge Contract Security  *(Severity: Medium · Status: Unresolved)*

The OptimismMintableERC20 token's entire supply mechanism relies on the `BRIDGE` address, which has exclusive permission to call the `mint` and `burn` functions. If the `BRIDGE` contract is compromised, an attacker could arbitrarily mint tokens, leading to hyperinflation and a complete loss of value for the token. This is an inherent design characteristic of a mintable bridged token, but it represents the single most significant risk to the system's economic integrity (7.4 Economic, 7.6 External).

**Recommendation:** Ensure the `BRIDGE` contract is secured with the highest possible standards, including comprehensive audits, robust access control (e.g., multi-signature wallets, time-locks), and continuous monitoring. The security posture of the `BRIDGE` contract directly dictates the security of this token.


### `L-01` — Interface Mismatch for `bridge()` Function View Mutability  *(Severity: Low · Status: Unresolved)*

The `IOptimismMintableERC20` interface declares the `bridge()` function as `external returns (address)`, omitting the `view` keyword. However, the `OptimismMintableERC20` implementation correctly defines it as `public view returns (address)`. While the implementation is more restrictive and correct, this minor inconsistency in the interface definition could lead to confusion or potential issues with static analysis tools expecting exact interface compliance (7.2 Code Security).

**Recommendation:** Update the `IOptimismMintableERC20` interface to include the `view` keyword for the `bridge()` function to accurately reflect its mutability and ensure full consistency with the implementation: `function bridge() external view returns (address);`.


### `I-01` — Effective Use of OpenZeppelin Libraries  *(Severity: Informational · Status: Resolved)*

The contract effectively utilizes battle-tested and audited OpenZeppelin contracts (ERC20, IERC165). This practice significantly reduces the risk of common vulnerabilities and improves the overall security posture of the contract by relying on widely accepted and secure implementations (7.2 Code Security).

**Recommendation:** Continue to leverage well-vetted libraries like OpenZeppelin for standard functionalities. Ensure that the specific versions used are up-to-date and free from known vulnerabilities.


### `I-02` — Immutable Critical Parameters  *(Severity: Informational · Status: Resolved)*

The `REMOTE_TOKEN`, `BRIDGE`, and `DECIMALS` variables are declared as `immutable` and initialized in the constructor. This is a strong security practice as it ensures these critical parameters cannot be altered after deployment, preventing unauthorized changes to the token's fundamental configuration (7.2 Code Security, 7.3 Access Control).

**Recommendation:** Maintain the use of `immutable` for all critical parameters that should not change post-deployment. This enhances security and predictability.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x624e...8831`](https://basescan.org/address/0x624e2e7fdc8903165f64891672267ab0fcb98831) |
| **Network** | Base |
| **Price** | $0.331 |
| **24h Volume** | $851.7K |
| **Liquidity** | $230.2K |
| **Volume / Liquidity** | 3.7× |
| **Token Age** | 8mo |
| **Top-10 Holders** | 97.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 3788 buys / 3827 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/base/0x29183f918920a2aef0115a9c7374945589968aea)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/sosovalue-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-15*
