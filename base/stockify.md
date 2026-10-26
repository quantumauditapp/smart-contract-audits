---
token: Stockify
ticker: STFY
network: base
risk_score: 23
status: low
date: 2026-08-30
---

# Stockify (STFY) — Smart Contract Security Analysis | Base

> **Risk Score: 23/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/stockify-base)

---

## Audit Summary

The StockifyToken contract implements an ERC20 token with a custom holder tracking mechanism. The contract is generally well-structured and uses OpenZeppelin libraries. Key functionalities include owner-controlled adjustments to minimum share balance and exclusion from rewards. The primary risks identified relate to the centralized control over key parameters and the use of an EOA for ownership.

> **Final Recommendation:** To enhance the security posture, consider transitioning the contract ownership from an EOA to a multi-signature wallet or a robust governance contract. This decentralizes control and mitigates the risk associated with a single point of failure. Additionally, clearly document the intended use and implications of the `_holders` array and the owner's control over its parameters to ensure transparency for users and stakeholders.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The StockifyToken contract demonstrates strong technical foundations, leveraging battle-tested OpenZeppelin ERC20 and Ownable implementations. The custom `_syncHolder` logic for managing the… |
| **Governance / Economics** | 6/10 | Medium | The economic model is based on a fixed total supply ERC20 token. The owner has significant control over parameters that define who is considered a 'holder' (7.4 Economic). Specifically, the… |
| **Upgrades** | 7/10 | Low | The contract is not designed as an upgradeable proxy, meaning its logic cannot be modified post-deployment. This design choice eliminates upgrade-related risks such as proxy misconfigurations or… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Locked** | 86.2% — UNCX V4 Lock |
| **Top-1 Unlocked Holder** | 13.8% |

## Security Findings

_🟡 1 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `M-01` — Centralized Control over Holder List Parameters  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract owner has the ability to set `minShareBalance` and manually `rewardsExcluded` addresses. These functions directly influence which addresses are included in the `_holders` array. If this array is used for critical functions such as reward distribution, voting, or whitelisting, the owner possesses significant centralized control over these mechanisms, which could be abused to exclude legitimate holders or include favored addresses.

**Recommendation:** Consider decentralizing control over these parameters, perhaps through a multi-signature wallet, a time-locked contract, or a robust governance mechanism. Clearly document the intended use of the `_holders` array and the implications of owner control for all stakeholders.


### `L-01` — Owner EOA Risk  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract owner is an Externally Owned Account (EOA). If the private key for this EOA is compromised, an attacker could gain full control over the `setMinShareBalance` and `setRewardsExcluded` functions, potentially manipulating the holder list and any associated protocol mechanics.

**Recommendation:** Transfer ownership to a multi-signature wallet or a robust governance contract to mitigate the single point of failure risk associated with an EOA owner.


### `I-01` — Fixed `MIN_SHARE_BALANCE_FLOOR` and `MIN_SHARE_BALANCE_CEILING`  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `MIN_SHARE_BALANCE_FLOOR` and `MIN_SHARE_BALANCE_CEILING` constants are hardcoded in the contract. While this provides a bounded range for `minShareBalance`, it means the range itself cannot be adjusted without a contract redeployment. If future protocol needs require a different range, a new contract deployment would be necessary.

**Recommendation:** If flexibility is desired in the future, consider making these bounds configurable by the owner or governance. Otherwise, acknowledge that any changes to these limits would necessitate a new contract deployment.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xc640...7bf5`](https://basescan.org/address/0xc6405d7a226e1c18e559be2f335f74c01ad07bf5) |
| **Network** | Base |
| **Price** | $0.0006683 |
| **24h Volume** | $128.7K |
| **Liquidity** | $92.1K |
| **Volume / Liquidity** | 1.4× |
| **Token Age** | 10d |
| **Top-10 Holders** | 26.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 235 buys / 123 sells |

## Security Flags (4/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/base/0xa6979745954ea4976d4c94a5957c225801de74b4ef6ab22d122854fb09405e06)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/stockify-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-30*
