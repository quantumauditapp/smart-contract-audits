---
token: 00 Token
ticker: 00
network: ethereum
risk_score: 54
status: high
date: 2026-08-13
---

# 00 Token (00) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 54/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/00-token-eth)

---

## Audit Summary

The P00lsTokenCreator contract serves as an ERC-20 token with Merkle drop functionality, deployed as an upgradeable implementation behind a BeaconProxy. It leverages OpenZeppelin's upgradeable contracts and a RegistryOwnable pattern for access control. While the core ERC-20 and Merkle drop logic appears sound, a significant design decision grants unlimited allowance to an external `xCreatorToken` contract, posing a high economic risk if that dependency is compromised. Minor informational findings relate to upgradeability nuances and external dependencies.

> **Final Recommendation:** Prioritize addressing the high-severity finding regarding the unlimited allowance granted to `xCreatorToken`. Evaluate if this level of trust is absolutely necessary and explore alternative, more granular approval mechanisms or robust security measures for `xCreatorToken`. Pin the Solidity pragma to a specific version to ensure consistent compilation. Review the necessity of the `initializer()` call in the constructor of the implementation contract for clarity, although it poses no direct security risk.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract demonstrates good technical architecture, inheriting from well-audited OpenZeppelin upgradeable contracts for ERC-20, ERC-20Votes, Multicall, and ERC-1363 functionalities (7.1… |
| **Governance / Economics** | 3/10 | High | Access control is managed through a `RegistryOwnable` pattern, allowing for flexible and potentially multi-sig ownership, which is a robust approach (7.3 Access Control, 7.5 Governance). However, a… |
| **Upgrades** | 2/10 | High | The contract is designed as an upgradeable implementation for a BeaconProxy, correctly utilizing OpenZeppelin's `initializer()` modifier to prevent re-initialization on upgrades (7.7 Upgrades). All… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Etherscan Detected Custom |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 52.8% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟢 1 Low · ⚪ 2 Informational_

### `H-01` — Unlimited Allowance Granted to `xCreatorToken`  *(Severity: High · Status: Unresolved)*

The `allowance` function in `P00lsTokenCreator` is overridden to return `type(uint256).max` for the `xCreatorToken` address. This design choice grants the `xCreatorToken` contract unlimited spending approval over all token holders' balances within this contract. This represents a significant trust assumption and a potential single point of failure. If `xCreatorToken` is compromised, exploited, or behaves maliciously, it could lead to the draining of all `P00lsTokenCreator` tokens from users who have approved this contract.

**Recommendation:** Re-evaluate the necessity of granting unlimited allowance to `xCreatorToken`. If possible, implement a more granular allowance mechanism (e.g., specific amounts, time-bound approvals, or a pull-based system). If unlimited allowance is critical for functionality, ensure `xCreatorToken` undergoes rigorous security audits, has robust access control, and is managed by a highly secure entity (e.g., a multi-sig or DAO). Consider implementing circuit breakers or emergency pause mechanisms in `xCreator…


### `L-01` — Broad Solidity Pragma Version  *(Severity: Low · Status: Unresolved)*

The contract uses `pragma solidity ^0.8.0;`. This allows compilation with any `0.8.x` version. While minor version updates are generally backward-compatible, it is a best practice to pin the pragma to a specific compiler version (e.g., `pragma solidity 0.8.13;`) to ensure consistent bytecode generation and avoid potential issues with future compiler updates that might introduce subtle changes or new warnings.

**Recommendation:** Pin the Solidity pragma to a specific compiler version used for deployment, for example, `pragma solidity 0.8.13;` to ensure consistent compilation results.


### `I-01` — Constructor `initializer()` Call in Upgradeable Implementation  *(Severity: Informational · Status: Unresolved)*

The `P00lsTokenCreator` constructor calls `initializer()`. In a BeaconProxy setup, the constructor of the implementation contract is called only once upon its deployment, not when the proxy is initialized. The `initialize` function, which also uses `initializer()`, is the one called via the proxy to set up the contract's state. While this constructor call is harmless as it only sets an internal flag that `initialize` also sets, it is redundant and can be confusing. The primary protection against re-initialization for proxy contracts comes from the `initializer` modifier on the `initialize` function itself.

**Recommendation:** Consider removing the `initializer()` call from the constructor of the implementation contract, as it is not strictly necessary for the proxy's upgradeability logic and can be misleading. The `initialize` function's `initializer()` modifier is sufficient.


### `I-02` — Inter-Contract Dependency on `xCreatorToken` Security  *(Severity: Informational · Status: Unresolved)*

The `P00lsTokenCreator` contract has a strong dependency on the `xCreatorToken` contract. Specifically, the `_delegate` function mirrors delegation calls to `xCreatorToken.__delegate`, and `xCreatorToken` is granted unlimited allowance (as noted in H-01). This tight coupling means that the overall security and integrity of `P00lsTokenCreator` are directly tied to the security and trustworthiness of `xCreatorToken`. Any vulnerability, exploit, or malicious behavior within `xCreatorToken` could directly impact `P00lsTokenCreator` and its users.

**Recommendation:** Ensure that the `xCreatorToken` contract undergoes equally rigorous security audits and adheres to the highest security standards. Implement robust monitoring for `xCreatorToken`'s behavior and consider mechanisms to decouple or mitigate risks associated with this dependency if possible.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x881b...250d`](https://etherscan.io/address/0x881ba05de1e78f549cc63a8f6cabb1d4ad32250d) |
| **Network** | Ethereum |
| **Price** | $0.009741 |
| **24h Volume** | $64.7K |
| **Liquidity** | $271.9K |
| **Volume / Liquidity** | 0.2× |
| **Token Age** | 1y |
| **Top-10 Holders** | 91.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 125 buys / 89 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x896f9772345a1fc3eb98aed0c129dfc4c8de3654b603ea50d70ae56395876756)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/00-token-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-13*
