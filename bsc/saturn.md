---
token: Saturn
ticker: SATURN
network: bsc
risk_score: 33
status: low
date: 2026-09-02
---

# Saturn (SATURN) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 33/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/saturn-bsc)

---

## Audit Summary

The FlapTaxTokenV3 contract implements an upgradeable ERC20 token with a dynamic tax mechanism and a multi-state pool system. The contract utilizes OpenZeppelin's upgradeable patterns and SafeERC20 for secure token operations. However, a critical portion of the `_liquidateTax` function, which is central to the token's economic logic and state transitions, was truncated in the provided source code, preventing a complete security assessment of this core functionality. This significantly elevates the overall risk level.

> **Final Recommendation:** It is imperative to provide the complete source code for the `_liquidateTax` function to enable a comprehensive security assessment of the token's core economic and operational logic. Additionally, consider implementing multi-signature wallets or time-locks for critical owner-controlled functions to mitigate risks associated with centralized control. Thoroughly review the complex state machine logic to ensure all transitions and conditions are robust and free from unintended behavior.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract leverages well-audited OpenZeppelin libraries for ERC20, access control (Ownable), and upgradeability (Initializable), enhancing code security (7.2 Code Security). The use of `SafeERC20`… |
| **Governance / Economics** | 7/10 | Low | The contract employs an `OwnableUpgradeable` pattern, granting the owner significant control over critical functions like `startMigration` and `finalizeMigration`, which directly influence the… |
| **Upgrades** | 4/10 | Medium | The contract is designed for upgradeability using OpenZeppelin's `Initializable` pattern, correctly employing `_disableInitializers()` in the constructor and `initializer` modifier for the… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Etherscan Detected Custom |
| **Implementation** | ✅ Verified source |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Null Address |

## Security Findings

_🔴 1 Critical · 🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `C-01` — Incomplete `_liquidateTax` Function Analysis  *(Severity: Critical · Status: Unresolved)*

The provided source code for the `_liquidateTax` function is truncated. This function is invoked on every `_transfer` to the `mainPool` and is responsible for critical operations including `PoolState` transitions, tax distribution to `taxProcessor` and `dividendContract`, and potential swaps via `v2Router`. Without the complete implementation, it is impossible to assess fundamental security properties such as reentrancy vulnerabilities, potential denial-of-service conditions, integer overflows/underflows in tax calculations or external interactions, and overall economic integrity.

**Recommendation:** Provide the full and complete source code for the `_liquidateTax` function to allow for a comprehensive security audit. A full audit of this function is essential to ensure the safety and correctness of the token's core economic mechanisms.


### `H-01` — Centralized Control by Owner  *(Severity: High · Status: Unresolved)*

The contract utilizes the `OwnableUpgradeable` pattern, granting the owner sole control over critical functions such as `startMigration` and `finalizeMigration`. These functions directly alter the `PoolState`, which in turn affects tax rates and transfer restrictions. This centralized control introduces a single point of failure, where a compromised owner key or a malicious owner could unilaterally change the token's operational parameters, potentially leading to economic manipulation or system disruption.

**Recommendation:** Consider implementing a multi-signature wallet for the owner address to distribute control among multiple trusted parties. For highly sensitive operations, explore adding time-locks to allow for community review or emergency intervention before changes take effect.


### `M-01` — Complex State Machine Logic  *(Severity: Medium · Status: Unresolved)*

The contract implements a complex state machine using the `PoolState` enum (BondingCurve, Migrating, TaxEnforcedAntiFarmer, TaxEnforced, TaxFree) with transitions managed within `_transfer` and `_liquidateTax`. The intricate conditions and order of checks for state changes, especially those dependent on `block.timestamp` and `pools` mapping, increase the likelihood of subtle logic errors or unintended state transitions. Such errors could lead to incorrect tax application, unexpected transfer restrictions, or economic imbalances.

**Recommendation:** Thoroughly review and test all state transitions and their associated conditions. Consider formal verification methods or extensive unit and integration testing to cover all possible state paths and edge cases. Document the state machine logic clearly to aid future understanding and maintenance.


### `L-01` — Potential for Front-running State Transitions  *(Severity: Low · Status: Unresolved)*

The `_liquidateTax` function triggers `PoolState` changes based on `block.timestamp` exceeding specific expiration times (`taxExpirationTime`, `antiFarmerExpirationTime`). If a state transition (e.g., from `TaxEnforced` to `TaxFree`) offers a significant economic advantage, malicious actors could monitor the mempool for transactions that would trigger these changes. They could then front-run such transactions to gain an unfair advantage by executing their own transactions (e.g., large trades) just before the state change occurs.

**Recommendation:** While `block.timestamp` is inherently susceptible to miner manipulation and front-running, for time-based state transitions, consider if the economic impact of front-running is acceptable. If not, explore alternative mechanisms that are less susceptible to front-running, such as commit-reveal schemes or batching transactions, though these often add complexity.


### `I-01` — Reliance on External Contracts  *(Severity: Informational · Status: Unresolved)*

The `FlapTaxTokenV3` contract relies on several external contracts, including `taxProcessor`, `dividendContract`, `v2Router`, and `quoteToken`. The security and trustworthiness of these external dependencies are paramount to the overall integrity of the system. Any vulnerabilities, malicious behavior, or incorrect configuration in these external contracts could directly impact the functionality and security of the `FlapTaxTokenV3` token.

**Recommendation:** Ensure that all external contract addresses are correctly configured and point to audited, trusted, and immutable contracts where possible. Implement robust validation for external contract addresses during initialization and any subsequent updates. Regularly monitor the security posture of all integrated external protocols.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xf23e...7777`](https://bscscan.com/address/0xf23e4a84a950e9adae4b95468a4857ca34ce7777) |
| **Network** | BNB Chain |
| **Price** | $0.0003759 |
| **24h Volume** | $398.1K |
| **Liquidity** | $70.2K |
| **Volume / Liquidity** | 5.7× |
| **Token Age** | 4d |
| **Top-10 Holders** | 28.8% of supply |
| **Buy / Sell Tax** | 1.0% / 1.0% |
| **24h Transactions** | 1483 buys / 1388 sells |

## Security Flags (4/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x9b389424b95ba97e4e00159cc6e1d0cb967d0fe2)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/saturn-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-02*
