---
token: Ice Open Network
ticker: ION
network: bsc
risk_score: 57
status: high
date: 2026-08-11
---

# Ice Open Network (ION) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 57/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/ice-open-network-bsc)

---

## Audit Summary

The Bridge contract facilitates cross-chain asset transfers using a multi-signature oracle system. It allows for minting wrapped tokens, updating the oracle set, and controlling burn functionality, all governed by a 2/3 majority vote of the current oracle set. While the core voting mechanism is robust, the system's security heavily relies on the integrity of the oracle set. Potential denial-of-service vectors exist if the oracle set grows excessively large, impacting critical administrative functions. The contract is not upgradeable, which simplifies upgrade safety but requires careful initial deployment.

> **Final Recommendation:** It is strongly recommended to carefully manage the size and security of the oracle set, as it represents the single point of trust for the bridge's operations. Implement a maximum limit for the number of oracles to mitigate the denial-of-service vulnerability in administrative functions. Consider pinning the Solidity compiler version to a specific patch release to ensure consistent compilation behavior. For long-term sustainability, evaluate the implications of non-upgradeability and plan for potential future migrations if the protocol evolves or critical issues arise.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 7/10 | Low | The technical implementation demonstrates good practices such as requiring sorted signatures and preventing vote replays (7.2 Code Security). The contract correctly implements a 2/3 majority… |
| **Governance / Economics** | 6/10 | Medium | The economic and governance model is highly centralized around the oracle set (7.4 Economic, 7.5 Governance). While a 2/3 majority is required for all critical actions, including updating the oracle… |
| **Upgrades** | 5/10 | Medium | The Bridge contract is not designed with an upgrade mechanism (7.7 Upgrades). This eliminates risks associated with proxy patterns, such as storage collisions or incorrect upgrade paths. However, it… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Locked** | 100.0% — UNCX Locker |
| **Top-1 Unlocked Holder** | 0.0% |

## Security Findings

_🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 2 Informational_

### `H-01` — High Centralization Risk via Oracle Set  *(Severity: High · Status: Unresolved)*

The security and integrity of the entire bridge system are fundamentally dependent on the honesty and operational security of the `oraclesSet`. A 2/3 majority of these oracles can collectively approve any minting operation, change the oracle set itself, or toggle the burn status. If a majority of oracles are compromised or collude, they gain complete control over the wrapped token supply and bridge operations, leading to potential arbitrary minting and asset loss. This is a core design decision but represents a significant trust assumption (7.4 Economic, 7.5 Governance, 7.6 External).

**Recommendation:** While this is a design choice, ensure the oracle set is composed of diverse, reputable, and geographically distributed entities. Implement robust operational security procedures for each oracle. Consider exploring mechanisms for further decentralization or introducing additional layers of security (e.g., time locks for critical changes, community oversight) in future iterations if feasible.


### `M-01` — Potential Denial-of-Service (DoS) via Large Oracle Set  *(Severity: Medium · Status: Unresolved)*

The `updateOracleSet` function contains two loops that iterate over the `oraclesSet` array, and the `generalVote` function iterates over the `signatures` array. If the number of oracles (and consequently, the number of required signatures) grows excessively large, these loops could consume more gas than the block gas limit, rendering critical administrative functions like `voteForNewOracleSet` and other voting mechanisms unusable. This would effectively prevent the oracle set from being updated or any new votes from being processed, leading to a denial of service for the bridge's governance (7.2 Code Security, 7.8 Operations).

**Recommendation:** Implement a maximum limit for the size of the `oraclesSet` to ensure that loop iterations remain within reasonable gas limits. Carefully calculate the maximum feasible oracle count based on current and projected gas costs. Consider alternative data structures or batching mechanisms for very large sets if a high number of oracles is a strict requirement.


### `L-01` — Unpinned Solidity Pragma  *(Severity: Low · Status: Unresolved)*

The contract uses a floating Solidity pragma `^0.7.0`. This allows it to be compiled with any compiler version from 0.7.0 up to, but not including, 0.8.0. While generally safe, using a floating pragma can lead to unexpected behavior if a new compiler version introduces subtle changes or bugs that affect the contract's logic. It's best practice to pin the pragma to a specific, tested compiler version (e.g., `pragma solidity 0.7.6;`) (7.2 Code Security).

**Recommendation:** Pin the Solidity compiler version to a specific, known-good version (e.g., `pragma solidity 0.7.6;`) to ensure consistent compilation and deployment behavior across different environments and over time.


### `I-01` — Use of `pragma experimental ABIEncoderV2`  *(Severity: Informational · Status: Unresolved)*

The contract uses `pragma experimental ABIEncoderV2;`. While `ABIEncoderV2` has been standard since Solidity 0.8.0, its explicit `experimental` declaration in 0.7.x versions was common. This is generally stable but is a historical note regarding compiler features (7.2 Code Security).

**Recommendation:** No direct action is required as this is a historical pragma. For future contracts, using Solidity 0.8.0 or higher would make this pragma unnecessary.


### `I-02` — Oracle Set Size Comment Not Enforced  *(Severity: Informational · Status: Unresolved)*

The comment in `generalVote` states: `// NOTE: In practice, the number of oracles should be chosen to be divisible by 3.` This is a good operational guideline for ensuring clean 2/3 majority calculations, but it is not enforced by the contract's code. The current implementation correctly handles non-divisible numbers using integer division (floor) (7.2 Code Security, 7.8 Operations).

**Recommendation:** Consider adding a `require` statement in `updateOracleSet` to enforce that `newSet.length` is divisible by 3, if this is a strict operational requirement. Otherwise, ensure all stakeholders understand that the 2/3 consensus uses floor division for non-divisible numbers.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xe1ab...5ea8`](https://bscscan.com/address/0xe1ab61f7b093435204df32f5b3a405de55445ea8) |
| **Network** | BNB Chain |
| **Price** | $0.00007675 |
| **24h Volume** | $45.9K |
| **Liquidity** | $196.8K |
| **Volume / Liquidity** | 0.2× |
| **Token Age** | 5mo |
| **Top-10 Holders** | 56.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 911 buys / 1356 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x6487725b383954e05ca56f3c2b93a104b3dd2c25)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/ice-open-network-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-11*
