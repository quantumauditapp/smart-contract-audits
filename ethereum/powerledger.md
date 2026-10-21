---
token: PowerLedger
ticker: POWR
network: ethereum
risk_score: 67
status: high
date: 2026-09-12
---

# PowerLedger (POWR) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 67/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/powerledger-eth)

---

## Audit Summary

The PowerLedger contract implements an ERC20-like token. The audit identified several high-severity issues related to the ERC20 `approve` race condition and centralized administrative control, alongside medium-severity concerns regarding the use of an outdated Solidity compiler. While basic token functionalities are present, the contract's age and specific design choices introduce notable security risks.

> **Final Recommendation:** It is strongly recommended to migrate the contract to a modern Solidity compiler version (e.8.x) to leverage automatic safety checks and improved error handling. Address the ERC20 `approve` race condition by implementing a safer allowance modification pattern. Furthermore, enhance the security of the `migrationInfoSetter` role by considering multi-signature control or time-locks for critical administrative actions to mitigate centralization risks.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract implements a basic ERC20-like token with standard transfer functionalities. Strengths include explicit checks to prevent integer underflows in transfer operations (7.2 Code Security).… |
| **Governance / Economics** | 1/10 | High | The contract features a `migrationInfoSetter` role, which can update an informational string and, critically, transfer its own administrative privileges (7.3 Access Control). This design introduces a… |
| **Upgrades** | 6/10 | Medium | The contract is not designed with upgradeability patterns (e.g., proxy contracts) and is immutable once deployed (7.7 Upgrades). This eliminates upgrade-related risks such as proxy misconfigurations… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 99.9% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 2 High · 🟡 1 Medium · 🟢 1 Low_

### `H-01` — ERC20 `approve` Race Condition  *(Severity: High · Status: Unresolved)*

The `approve` function is vulnerable to a known ERC20 race condition. If a user approves an allowance and then attempts to change it, a malicious spender can front-run the second transaction to spend the original allowance, then the new allowance is set, allowing the spender to spend more than intended. While `compareAndApprove` attempts to mitigate this by checking `_currentValue`, it does not fully resolve the issue in all scenarios, especially when increasing allowances or if the spender is also front-running the `compareAndApprove` call itself. (7.2 Code Security)

**Recommendation:** Implement the 'approve-and-call' pattern or require setting allowance to zero before increasing it. For `compareAndApprove`, ensure its logic is robust against all race conditions or deprecate it in favor of a safer pattern that explicitly sets allowance to zero before a new value is approved.


### `H-02` — Centralized Administrative Control  *(Severity: High · Status: Unresolved)*

The `migrationInfoSetter` role has the authority to change itself (`changeMigrationInfoSetter`) and set arbitrary `migrationInfo` (`setMigrationInfo`). This introduces a single point of failure. If the `migrationInfoSetter` address is compromised, an attacker could transfer the role to themselves and then set misleading `migrationInfo`, potentially for phishing or social engineering attacks. (7.3 Access Control, 7.4 Economic)

**Recommendation:** Consider implementing a multi-signature wallet for the `migrationInfoSetter` role or a time-locked mechanism for critical administrative changes like `changeMigrationInfoSetter` to reduce the risk of a single point of compromise and provide a window for intervention.


### `M-01` — Outdated Solidity Compiler Version  *(Severity: Medium · Status: Unresolved)*

The contract is compiled with Solidity version `0.4.11`. This version is significantly outdated and lacks several security features, gas optimizations, and robust error handling mechanisms (e.g., `require`, `revert`, `assert`) introduced in later versions. While explicit checks mitigate direct integer underflows in `transfer` and `transferFrom`, the general use of an old compiler version increases the risk of undiscovered compiler bugs or less secure code patterns. (7.2 Code Security)

**Recommendation:** Migrate the contract to a more recent and supported Solidity compiler version (e.g., 0.8.x) to benefit from automatic overflow/underflow checks, improved error handling, and other security enhancements. Thoroughly re-audit the contract after migration to ensure no new vulnerabilities are introduced.


### `L-01` — Missing Event for Critical State Change  *(Severity: Low · Status: Unresolved)*

The `changeMigrationInfoSetter` function, which modifies a critical administrative role, does not emit an event. This makes it difficult to monitor and track changes to the `migrationInfoSetter` address on-chain, hindering transparency and off-chain auditing. (7.2 Code Security, 7.8 Operations)

**Recommendation:** Emit an event (e.g., `event MigrationInfoSetterChanged(address indexed oldSetter, address indexed newSetter);`) whenever the `migrationInfoSetter` address is updated to improve transparency and traceability of administrative actions.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x5958...1269`](https://etherscan.io/address/0x595832f8fc6bf59c85c527fec3740a1b7a361269) |
| **Network** | Ethereum |
| **Price** | $0.055 |
| **24h Volume** | $44.2K |
| **Liquidity** | $535.9K |
| **Volume / Liquidity** | 0.1× |
| **Token Age** | 4y |
| **Top-10 Holders** | 80.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 215 buys / 183 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0xe3fe800b0de664bf0bca8ad58ecbc73b259047b0)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/powerledger-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-12*
