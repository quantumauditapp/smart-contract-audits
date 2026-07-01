---
token: Gram (prev. Toncoin)
ticker: GRAM
network: ethereum
risk_score: 100
status: critical
date: 2026-06-30
---

# Gram (prev. Toncoin) (GRAM) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 100/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/gram-prev-toncoin-eth)

---

## Audit Summary

The TON Bridge contract implements a multi-signature oracle system for cross-chain operations, including token minting and oracle set management. The architecture relies on a 2/3 majority of designated oracles for critical decisions. While the core voting mechanism is robust against replay attacks, significant centralization risk exists due to the oracle-based governance model. Potential Denial of Service (DoS) in oracle set updates and the use of an older Solidity version are also noted. The contract is not upgradeable, ensuring immutability but limiting future flexibility.

> **Final Recommendation:** The TON Bridge contract provides a functional multi-signature bridge, but its security is heavily dependent on the integrity of the oracle set. Addressing the potential Denial of Service in oracle set updates and considering an upgrade to a more recent Solidity version are recommended to enhance robustness. The project should also clearly communicate the inherent centralization risks associated with its oracle-based governance model to its users.

For enhanced security and ongoing monitoring, consider a Premium Deploy option. This includes continuous threat monitoring, real-time anomaly detection, and rapid incident response, providing an additional layer of protection for the deployed contract.

## Security Analysis

The TON Bridge contract implements a multi-signature oracle system for cross-chain operations, including token minting and oracle set management. The architecture relies on a 2/3 majority of designated oracles for critical decisions. While the core voting mechanism is robust against replay attacks, significant centralization risk exists due to the oracle-based governance model. Potential Denial of Service (DoS) in oracle set updates and the use of an older Solidity version are also noted. The contract is not upgradeable, ensuring immutability but limiting future flexibility.

The TON Bridge contract provides a functional multi-signature bridge, but its security is heavily dependent on the integrity of the oracle set. Addressing the potential Denial of Service in oracle set updates and considering an upgrade to a more recent Solidity version are recommended to enhance robustness. The project should also clearly communicate the inherent centralization risks associated with its oracle-based governance model to its users.

For enhanced security and ongoing monitoring, consider a Premium Deploy option. This includes continuous threat monitoring, real-time anomaly detection, and rapid incident response, providing an additional layer of protection for the deployed contract.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 4/10 | Medium | The contract demonstrates a robust multi-signature architecture (7.1) for critical operations, requiring a 2/3 majority of oracles for actions like minting and oracle set updates. Code security (7.2)  |
| **Governance / Economics** | 3/10 | High | The governance model (7.5) is based on a centralized oracle set, where a 2/3 majority controls all critical functions, including token minting and the ability to update the oracle set itself. This des |
| **Upgrades** | 4/10 | Medium | The `Bridge` contract is implemented as a standard contract without an explicit upgrade mechanism (7.7). This design choice eliminates upgrade-related risks such as proxy misconfigurations or maliciou |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 53.0% |
| **Top-3 Unlocked** | 74.8% |

## Security Findings

_🟠 1 High · 🟡 1 Medium · 🟢 2 Low · ⚪ 1 Informational_

### `H-01` — Centralization Risk / Oracle Collusion  *(Severity: High · Status: Unresolved)*

The system's security and integrity are entirely dependent on a 2/3 majority of the `oraclesSet`. If 2/3 or more of the designated oracles collude, they can perform unauthorized actions such as minting arbitrary amounts of tokens via `voteForMinting`, changing the oracle set to include malicious actors via `voteForNewOracleSet`, or disabling burning via `voteForSwitchBurn`. This represents a significant centralization risk (7.4, 7.5).

**Recommendation:** While this is a fundamental design choice for a multi-signature bridge, it is crucial to acknowledge and mitigate this risk through robust oracle selection processes, transparent governance, and potentially diversifying oracle responsibilities. Consider implementing a timelock for critical operations like `updateOracleSet` to allow for community review and reaction time.


### `M-01` — Potential Denial of Service (DoS) in `updateOracleSet`  *(Severity: Medium · Status: Unresolved)*

The `updateOracleSet` function iterates through the `oraclesSet` twice using `for` loops. If the number of oracles in `oraclesSet` (both `oldSetLen` and `newSetLen`) grows excessively large, the gas cost of these loops could exceed the block gas limit. This would prevent the oracle set from being updated, effectively leading to a Denial of Service (DoS) for a critical governance function (7.2).

**Recommendation:** Implement a mechanism to handle large oracle sets more efficiently. This could involve paginated updates, a Merkle tree approach to verify membership, or limiting the maximum size of the oracle set. For the current design, ensure that the maximum expected number of oracles does not lead to gas limit issues.


### `L-01` — Use of `pragma experimental ABIEncoderV2`  *(Severity: Low · Status: Unresolved)*

The contract uses `pragma experimental ABIEncoderV2`. While `ABIEncoderV2` has been stable and non-experimental since Solidity 0.8.0, its use in older compiler versions (0.7.x) can sometimes indicate less mature code or potential for unexpected behavior, although it is generally considered safe (7.2).

**Recommendation:** Consider upgrading the Solidity compiler version to 0.8.x or higher, where `ABIEncoderV2` is no longer experimental and is the default. This would remove the need for the experimental pragma and allow the contract to benefit from newer compiler features and optimizations.


### `L-02` — Older Solidity Version (0.7.0)  *(Severity: Low · Status: Unresolved)*

The contract is compiled with Solidity version `^0.7.0`. This version is older and lacks several security features and optimizations present in newer versions (e.g., 0.8.x), such as default checked arithmetic for `uint` operations (preventing overflow/underflow by default) and more robust error handling mechanisms (7.2).

**Recommendation:** Upgrade the Solidity compiler version to 0.8.x or higher. This will automatically enable checked arithmetic for `uint` types, reducing the risk of integer overflow/underflow vulnerabilities, and provide access to other compiler improvements and security enhancements. Ensure thorough testing after any compiler upgrade.


### `I-01` — Lack of Event Emission for `allowBurn` Status Change  *(Severity: Informational · Status: Unresolved)*

The `voteForSwitchBurn` function updates the `allowBurn` state variable but does not emit an event to signal this change. While the state is updated on-chain, the absence of an event makes it harder for off-chain systems, such as frontends, indexers, or monitoring tools, to efficiently track and react to changes in the burning status (7.8 Operations).

**Recommendation:** Emit an event, such as `BurnStatusChanged(bool newBurnStatus, int nonce)`, whenever the `allowBurn` state variable is modified. This improves transparency and allows for easier off-chain monitoring and integration.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x582d...def1`](https://etherscan.io/address/0x582d872a1b094fc48f5de31d3b73f2d9be47def1) |
| **Network** | Ethereum |
| **Price** | $1.6300 |
| **24h Volume** | $42.9K |
| **Liquidity** | $745.2K |
| **Volume / Liquidity** | 0.1× |
| **Token Age** | 4y |
| **Top-10 Holders** | 29.3% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 21 buys / 32 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x4b62fa30fea125e43780dc425c2be5acb4ba743b)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/gram-prev-toncoin-eth)
- Security data: [GoPlus Labs](https://gopluslabs.io)

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-30*
