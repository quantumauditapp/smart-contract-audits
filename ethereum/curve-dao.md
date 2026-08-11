---
token: Curve DAO
ticker: CRV
network: ethereum
risk_score: 49
status: high
date: 2026-08-11
---

# Curve DAO (CRV) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 49/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/curve-dao-eth)

---

## Audit Summary

This audit covers the Curve DAO Token (CRV) contract, an ERC-20 token with a custom piecewise-linear mining supply mechanism implemented in Vyper. The contract manages token transfers, approvals, and a defined inflation schedule. Due to the provided source code being truncated, a full verification of the `transferFrom` function was not possible, which introduces a significant limitation to the technical assessment.

> **Final Recommendation:** Ensure that the full, verified source code for all deployed contracts is available for comprehensive security audits. For contracts with centralized roles like `admin` and `minter`, implement robust multi-signature controls or time-locks to mitigate risks associated with a single point of failure. Regularly review the economic parameters and their long-term implications, especially for inflation models. While Vyper provides strong inherent security, continuous vigilance and adherence to best practices are crucial for maintaining contract integrity.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 7/10 | Low | The contract demonstrates strong technical foundations, leveraging Vyper's safety features for secure arithmetic operations and preventing common Solidity pitfalls (7.2 Code Security). Core ERC-20… |
| **Governance / Economics** | 1/10 | High | The contract's economic model is based on a transparent, piecewise-linear inflation schedule, designed to distribute tokens over time (7.4 Economic). The `admin` role has centralized control over… |
| **Upgrades** | 3/10 | High | The contract is not designed with upgradeability in mind, as it is a standard implementation without a proxy pattern (7.7 Upgrades). This eliminates risks associated with upgrade mechanisms, such as… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 66.3% |
| **Top-3 Unlocked** | ⚠️ 99.7% |

## Security Findings

_🟠 1 High · 🟡 1 Medium · ⚪ 3 Informational_

### `H-01` — Truncated Source Code for `transferFrom` Function  *(Severity: High · Status: Unresolved)*

The provided source code for the `transferFrom` function is incomplete (`self.ba...`). This prevents a full and accurate security assessment of this critical ERC-20 functionality, which is essential for token transfers initiated by approved third parties. Without the complete code, potential vulnerabilities such as incorrect allowance checks, reentrancy, or arithmetic errors cannot be ruled out.

**Recommendation:** Provide the complete and verified source code for all functions within the contract to enable a thorough security audit. Ensure that the `transferFrom` implementation correctly handles allowances, balances, and prevents reentrancy or integer issues.


### `M-01` — Centralized Control by Admin and Minter Roles  *(Severity: Medium · Status: Unresolved)*

The `admin` role has significant power, including the ability to set the `minter` address (once) and transfer the `admin` role itself via `set_admin`. The `minter` role, once set, controls the actual issuance of new tokens based on the contract's inflation schedule. This centralization of control introduces a single point of failure and potential for malicious or compromised actors to manipulate token supply or administrative privileges (7.3 Access Control).

**Recommendation:** Consider implementing multi-signature wallets for the `admin` and `minter` roles to distribute control and require multiple approvals for critical operations. Alternatively, implement time-locks for sensitive administrative actions to provide a window for community review and intervention.


### `I-01` — Precision Loss in Rate Calculation Due to Integer Division  *(Severity: Informational · Status: Unresolved)*

The `_update_mining_parameters` and `mintable_in_timeframe` functions perform rate calculations using integer division (`_rate = _rate * RATE_DENOMINATOR / RATE_REDUCTION_COEFFICIENT`). While Vyper's integer division truncates, the contract's comment `double-division with rounding made rate a bit less => good` indicates this is an intentional design choice to bias the rate downwards, which is generally safer than upwards. However, it's important to acknowledge that this introduces minor precision loss over many epochs (7.4 Economic).

**Recommendation:** No direct action is required as this appears to be an intentional design choice. Document this behavior clearly in external specifications and ensure its implications are understood by stakeholders. If higher precision is ever required, consider using fixed-point arithmetic libraries or alternative calculation methods.


### `I-02` — Hardcoded Loop Limit in `mintable_in_timeframe`  *(Severity: Informational · Status: Unresolved)*

The `mintable_in_timeframe` function uses a hardcoded loop limit of `for i in range(999)` to calculate future mintable supply. Given that `RATE_REDUCTION_TIME` is one year, this limits the calculation to approximately 999 years. While this is practically sufficient for the expected lifespan of the protocol, it is a fixed constraint that could theoretically be reached under extreme, long-term scenarios (7.1 Architecture).

**Recommendation:** No immediate action is required given the practical implications. For future designs, if an indefinite or extremely long-term calculation is needed, consider an iterative approach that can be called multiple times or a more gas-efficient mathematical series calculation if possible.


### `I-03` — Slight Supply Increase from Late `update_mining_parameters` Calls  *(Severity: Informational · Status: Unresolved)*

The `update_mining_parameters` function can be called by anyone, but if it's called late in an epoch (i.e., after the epoch boundary but before the next call), the `_available_supply` calculation will result in a slightly higher `start_epoch_supply` for the subsequent epoch. The contract comment `Total supply becomes slightly larger if this function is called late` acknowledges this design trade-off, which prioritizes decentralization of calls over perfect precision at epoch boundaries (7.4 Economic).

**Recommendation:** No direct action is required as this is a known and accepted design trade-off. Ensure this behavior is clearly communicated to users and stakeholders. The impact is likely negligible given the scale of the token supply and the frequency of calls.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xd533...cd52`](https://etherscan.io/address/0xd533a949740bb3306d119cc777fa900ba034cd52) |
| **Network** | Ethereum |
| **Price** | $0.2602 |
| **24h Volume** | $609.6K |
| **Liquidity** | $1.55M |
| **Volume / Liquidity** | 0.4× |
| **Token Age** | 3y |
| **Top-10 Holders** | 57.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 550 buys / 499 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x4ebdf703948ddcea3b11f675b4d1fba9d2414a14-0xf939e0a03fb07f59a73314e73794be0e57ac1b4e-0xd533a949740bb3306d119cc777fa900ba034cd52)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/curve-dao-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-11*
