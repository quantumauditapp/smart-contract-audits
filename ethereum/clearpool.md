---
token: Clearpool
ticker: CPOOL
network: ethereum
risk_score: 23
status: low
date: 2026-09-15
---

# Clearpool (CPOOL) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 23/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/clearpool-eth)

---

## Audit Summary

The Clearpool (CPOOL) token contract is a standard ERC-20 implementation with added Compound-style delegation features. The contract demonstrates robust security practices, including custom safe math for `uint96` and `uint32` types, and proper EIP-712 signature handling for delegation. No critical or high-severity vulnerabilities were identified. Minor informational and low-severity findings relate to design choices and best practices.

> **Final Recommendation:** The CPOOL contract is well-engineered and adheres to strong security practices. It is recommended to address the identified low-severity and informational findings to further enhance robustness and clarity. Specifically, consider updating the `getChainId()` implementation to use `block.chainid` for improved readability and safety. While the initial token distribution to a multisig is common, ensure the multisig's security practices are robust. Monitor gas costs for `getPriorVotes` in extreme scenarios, although current design mitigates most risks.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The CPOOL contract exhibits strong technical security. It implements custom `safe96`, `safe32`, `add96`, and `sub96` functions to prevent integer overflows and underflows, which is a significant… |
| **Governance / Economics** | 2/10 | High | The contract defines a fixed total supply of 1 billion CPOOL tokens, with initial distribution entirely to a specified multisig address (7.4 Economic). This initial centralization is a common… |
| **Upgrades** | 6/10 | Medium | The CPOOL contract is deployed as a standard, non-upgradeable contract (7.7 Upgrades). This design choice eliminates upgrade-related risks such as proxy implementation vulnerabilities or… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟢 2 Low · ⚪ 2 Informational_

### `L-01` — Initial Centralization of Total Supply  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). In the constructor, the entire `totalSupply` (1 billion tokens) is minted and assigned to a single `multisig` address. This means that at deployment, 100% of the token supply is controlled by this single address. While common for initial token distribution, it represents a significant point of centralization and control over the token's initial liquidity and distribution strategy.

**Recommendation:** Ensure the `multisig` address is secured with robust operational procedures, including strong key management, multi-factor authentication, and a sufficient number of signers. Clearly communicate the role and security measures of this `multisig` to the community. This is a standard practice, but its security is paramount.


### `L-02` — Potential for High Gas Costs in `getPriorVotes` with Many Checkpoints  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `getPriorVotes` function uses a binary search algorithm to find historical vote counts. While efficient for sorted data, if a delegatee accumulates an extremely large number of checkpoints (e.g., one per block over many years), the gas cost for accessing and iterating through the `checkpoints` mapping could become substantial. Although `numCheckpoints` is limited by `uint32`, practical gas limits might be hit before reaching the theoretical maximum, potentially leading to denial of service for this specific function for highly active delegatees.

**Recommendation:** Monitor the gas usage of `getPriorVotes` in production, especially for delegatees with a high number of checkpoints. While the current implementation is standard and generally efficient, consider if any edge cases could lead to prohibitive gas costs. No immediate code change is required, but awareness and monitoring are advised.


### `I-01` — Use of `uint96` for Core Balances and Votes  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract utilizes `uint96` for `balances`, `allowances`, and `votes` storage variables. This design choice is typically made to optimize gas usage by fitting values into smaller storage slots. However, it limits the maximum possible value for these quantities to `2^96 - 1`, which is approximately 7.92 x 10^28. While this is a very large number, it is smaller than the maximum value of `uint256`.

**Recommendation:** Ensure that all users and integrators are aware of the `uint96` limit for token balances and voting power. This is a design decision, and no direct action is required if the limit is acceptable for the protocol's long-term scale. Document this constraint clearly in external-facing documentation.


### `I-02` — `getChainId()` Implementation Using Assembly  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `getChainId()` function uses inline assembly (`assembly { chainId := chainid() }`) to retrieve the chain ID. While functional and common in older Solidity versions, Solidity 0.8.0 and later (which this contract uses) provide the `block.chainid` global variable, offering a more readable and safer way to access the chain ID without resorting to assembly.

**Recommendation:** Replace the assembly block in `getChainId()` with `return block.chainid;` for improved code clarity and to leverage native Solidity features. This is a minor best practice improvement.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x6676...fac5`](https://etherscan.io/address/0x66761fa41377003622aee3c7675fc7b5c1c2fac5) |
| **Network** | Ethereum |
| **Price** | $0.02497 |
| **24h Volume** | $396.8K |
| **Liquidity** | $74.1K |
| **Volume / Liquidity** | 5.4× |
| **Token Age** | 1y |
| **Top-10 Holders** | 51.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 751 buys / 703 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0x81aee07f99be78d88881fa6d98feff7555113635)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/clearpool-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-15*
