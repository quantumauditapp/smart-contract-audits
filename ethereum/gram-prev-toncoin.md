---
token: Gram (prev. Toncoin)
ticker: GRAM
network: ethereum
risk_score: 67
status: high
date: 2026-06-30
---

# Gram (prev. Toncoin) (GRAM) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 67/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/gram-prev-toncoin-eth)

---

## Audit Summary

The TONBridge Bridge contract implements a multi-signature oracle system for minting wrapped TON tokens, updating the oracle set, and controlling burn functionality. The system relies on a 2/3 majority vote from a dynamic set of oracles. A critical vulnerability was identified in the quorum calculation, significantly lowering the required number of signatures for a vote to pass. High risks are associated with the inherent centralization of the oracle system and potential for vote execution failures. Several medium and low-severity issues were also found, including the use of an outdated Solidity compiler version and a potential for vote finalization before action execution.

> **Final Recommendation:** It is strongly recommended to immediately address the critical quorum calculation vulnerability to ensure the integrity of the multi-signature scheme. All arithmetic operations involving sensitive thresholds should be thoroughly reviewed and tested. Consider upgrading to a newer Solidity compiler version (0.8.x) to benefit from automatic overflow/underflow checks and other security enhancements. Implement a more robust error handling mechanism for vote execution to prevent votes from being marked as finished if the subsequent action fails.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract demonstrates a clear architecture for a multi-signature bridge, leveraging inherited ERC20 and signature verification functionalities (7.1). However, a critical flaw exists in the quorum… |
| **Governance / Economics** | 1/10 | High | The economic model centers around the minting and burning of a wrapped token, controlled by a set of oracles. The primary economic risk stems from the centralization inherent in the oracle system; a… |
| **Upgrades** | 5/10 | Medium | The contract is not designed as an upgradeable proxy, therefore, no upgrade-specific risks or safety issues are present (7.7). |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 60.4% |
| **Top-3 Unlocked** | ⚠️ 81.4% |

## Security Findings

_🔴 1 Critical · 🟠 2 High · 🟡 2 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `C-01` — Incorrect Quorum Calculation for 2/3 Majority  *(Severity: Critical · Status: Unresolved)*

The `generalVote` function calculates the required number of signatures for a 2/3 majority using integer division: `signatures.length >= 2 * oraclesSet.length / 3`. This calculation incorrectly truncates the result, leading to a lower-than-intended quorum for many `oraclesSet.length` values. For example, with 2 oracles, it requires 1 signature instead of 2; with 4 oracles, it requires 2 signatures instead of 3. This significantly weakens the security of the multi-signature scheme, making it easier for a minority of oracles to pass votes.

**Recommendation:** Modify the quorum calculation to correctly implement ceiling division for 2/3 of the oracle set. The formula `(2 * oraclesSet.length + 2) / 3` should be used to ensure the correct number of signatures is required. Thoroughly test this change with various oracle set sizes.


### `H-01` — Centralization Risk and Oracle Compromise  *(Severity: High · Status: Unresolved)*

The entire security and integrity of the Bridge contract, including token minting, oracle set updates, and burn status control, relies on the honesty and security of the oracle set. A compromise or collusion of 1/3 + 1 oracles (e.g., 2 out of 3, or 3 out of 4 with the current bug) can lead to unauthorized minting of tokens, disabling of the burn mechanism, or taking full control of the oracle set. This represents a significant centralization risk inherent to the design.

**Recommendation:** While this is a fundamental design choice, it is crucial to acknowledge and mitigate the risks associated with oracle centralization. Implement robust off-chain security practices for oracle key management, multi-factor authentication, and continuous monitoring. Consider mechanisms for emergency pauses or community-driven overrides if a supermajority of oracles is compromised, though this would require significant architectural changes.


### `H-02` — Vote Finalization Before Action Execution  *(Severity: High · Status: Unresolved)*

In the `generalVote` function, the `finishedVotings[digest] = true` flag is set *before* the actual action (e.g., `executeMinting`, `updateOracleSet`, `allowBurn = newBurnStatus`) is performed. If the subsequent action reverts due to an unexpected condition (e.g., an internal error in `mint`, or a `require` statement failure in `updateOracleSet`), the vote will still be marked as finished. This prevents any retry for that specific digest, potentially leaving a valid vote in a 'stuck' state where the action was intended but never completed.

**Recommendation:** Refactor the `generalVote` function to set `finishedVotings[digest] = true` *after* the successful execution of the associated action. This ensures that a vote is only marked as complete if its intended effect has been successfully applied to the contract state. Alternatively, implement a mechanism to allow a failed vote to be retried or explicitly cancelled by a supermajority.


### `M-01` — Outdated Solidity Compiler Version  *(Severity: Medium · Status: Unresolved)*

The contract uses Solidity `^0.7.0` and `^0.7.4`. These versions do not include automatic overflow and underflow checks for unsigned integers, which are standard in Solidity 0.8.0 and later. While no direct overflow/underflow vulnerabilities were identified in critical arithmetic beyond the quorum calculation, relying on older compiler versions increases the risk of subtle arithmetic bugs and misses out on other security improvements and optimizations present in newer versions.

**Recommendation:** Consider upgrading the contract to Solidity 0.8.x. This would provide automatic overflow/underflow checks, reducing the need for manual `SafeMath` implementations or extensive manual checks. A thorough review and testing process would be required to ensure compatibility and address any breaking changes introduced by the newer compiler version.


### `M-02` — `oracleSetHash` Parameter Unused in `updateOracleSet`  *(Severity: Medium · Status: Unresolved)*

The `voteForNewOracleSet` function takes an `int oracleSetHash` parameter, which is used to generate the digest for the vote. However, the `updateOracleSet` function, which is called after a successful vote, receives this `oracleSetHash` but does not use it to verify the `newSet` array. While the `newSet` itself is part of the digest and directly applied, the `oracleSetHash` parameter could be misleading if it implies a verification that does not occur within the `updateOracleSet` function.

**Recommendation:** Clarify the purpose of `oracleSetHash`. If it's purely an identifier for the vote, consider renaming it to avoid confusion. If it's intended to be a hash of the `newSet` for verification, implement the corresponding check within `updateOracleSet`. Ensure documentation clearly explains its role.


### `L-01` — Initial Oracle Set Not Subject to Vote  *(Severity: Low · Status: Unresolved)*

The `constructor` of the Bridge contract directly calls `updateOracleSet` with the `initialSet` provided during deployment. This means the initial set of oracles is established without any multi-signature vote. While this is a standard practice for contract initialization, it places full trust in the deployer to correctly and securely configure the initial oracle set.

**Recommendation:** Ensure that the deployment process is highly secure and that the `initialSet` of oracles is carefully chosen and verified. Document this trust assumption clearly for users and stakeholders. This is generally acceptable for bootstrapping a system.


### `I-01` — `experimental ABIEncoderV2` Pragma Used  *(Severity: Informational · Status: Unresolved)*

The contract uses `pragma experimental ABIEncoderV2;`. While ABIEncoderV2 has been widely adopted and is considered stable in practice, it was an experimental feature in Solidity 0.7.x. In Solidity 0.8.0 and later, it is enabled by default and the pragma is no longer necessary.

**Recommendation:** This is an informational note. If upgrading to Solidity 0.8.x, this pragma can be removed. No immediate action is required for functionality or security in 0.7.x, but it's a reminder of the compiler version's experimental features.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x582d...def1`](https://etherscan.io/address/0x582d872a1b094fc48f5de31d3b73f2d9be47def1) |
| **Network** | Ethereum |
| **Price** | $1.5500 |
| **24h Volume** | $4.2K |
| **Liquidity** | $784.6K |
| **Volume / Liquidity** | 0.0× |
| **Token Age** | 4y |
| **Top-10 Holders** | 29.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 21 buys / 32 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x4b62fa30fea125e43780dc425c2be5acb4ba743b)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/gram-prev-toncoin-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-30*
