---
token: Ampleforth Governance
ticker: FORTH
network: ethereum
risk_score: 42
status: medium
date: 2026-09-13
---

# Ampleforth Governance (FORTH) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 42/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/ampleforth-governance-eth)

---

## Audit Summary

The Forth token contract implements an ERC-20 compliant token with additional governance features, including delegation and vote checkpoints. It incorporates a controlled minting mechanism and burning functionalities. The contract demonstrates good code quality, utilizing SafeMath and EIP-712 for signed operations. Key areas of concern include the centralized control held by the `minter` address and the use of an older Solidity compiler version with experimental features. The contract is not upgradeable, which eliminates upgrade-specific risks.

> **Final Recommendation:** It is recommended to consider implementing a multi-signature wallet or a time-locked contract for the `minter` role to mitigate the risks associated with centralized control over token minting and minter address changes. This would enhance security by requiring multiple approvals for critical operations. Additionally, while the `uint96` usage is currently safe, a thorough review of potential edge cases with very large `totalSupply` values and their interaction with `uint` to `uint96` conversions is advised.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract demonstrates good adherence to ERC-20 standards and incorporates robust governance features like delegation and vote checkpoints (7.1 Architecture). It utilizes `SafeMath` for arithmetic… |
| **Governance / Economics** | 2/10 | High | The token's economic model includes a controlled minting mechanism with a `minter` role, a `mintCap` of 2% of total supply, and a `minimumTimeBetweenMints` of one year (7.4 Economic). This provides a… |
| **Upgrades** | 6/10 | Medium | The Forth contract is implemented as a standard, non-upgradeable token contract (7.7 Upgrades). This design choice eliminates the complexities and risks associated with proxy patterns and… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 59.9% |
| **Top-3 Unlocked** | ⚠️ 83.9% |

## Security Findings

_🟡 2 Medium · 🟢 2 Low · ⚪ 1 Informational_

### `M-01` — Minter's Ability to Manipulate Minting Schedule  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `mintingAllowedAfter` timestamp is updated to `block.timestamp + minimumTimeBetweenMints` after every `mint` operation. This means the `minter` can effectively reset the cooldown period by performing a small, insignificant mint. If the `minter` wishes to delay a larger, scheduled mint, they could execute a minimal mint transaction, pushing the next available minting window back by `minimumTimeBetweenMints` (one year). This could lead to unexpected delays in token distribution or inflation schedule (7.4 Economic, 7.8 Operations).

**Recommendation:** Consider modifying the `mintingAllowedAfter` logic to be less susceptible to manipulation. For example, `mintingAllowedAfter` could be set to `max(mintingAllowedAfter, block.timestamp) + minimumTimeBetweenMints` or a more robust schedule could be implemented that is not solely dependent on the last minting event.


### `M-02` — Centralized Minter Control  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `minter` address has significant centralized control over the token supply. This address can mint new tokens up to the `mintCap` (2% of total supply) annually and can also change the `minter` address itself via the `setMinter` function. A compromise of this single address could lead to uncontrolled inflation or a complete loss of control over the token's minting mechanism, directly impacting the token's economic stability and trust (7.3 Access Control, 7.4 Economic, 7.5 Governance).

**Recommendation:** Implement a multi-signature wallet (e.g., Gnosis Safe) or a time-locked contract for the `minter` role. This would require multiple trusted parties to approve critical operations like minting or changing the minter, significantly reducing the risk of a single point of failure.


### `L-01` — Use of Experimental ABIEncoderV2  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract uses `pragma experimental ABIEncoderV2;` with Solidity 0.6.11. While `ABIEncoderV2` has become standard and is widely used, its 'experimental' tag in older compiler versions implies that it might have had less rigorous auditing or could contain subtle bugs compared to fully stable features. Although unlikely to be a critical issue today, it's generally safer to use stable features or newer compiler versions where `ABIEncoderV2` is no longer experimental (7.2 Code Security).

**Recommendation:** For future deployments or upgrades, consider migrating to a newer Solidity compiler version (e.g., 0.8.x) where `ABIEncoderV2` is stable and no longer requires the experimental pragma. This would also benefit from other security enhancements in newer compilers.


### `L-02` — Older Solidity Compiler Version  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract is compiled with Solidity version 0.6.11. Newer Solidity versions (e.g., 0.8.x) include several security enhancements, such as built-in overflow/underflow checks for arithmetic operations, which reduce reliance on external libraries like SafeMath. While SafeMath is used here, migrating to a newer compiler could simplify the code and benefit from the latest compiler-level security features and optimizations (7.2 Code Security).

**Recommendation:** Consider upgrading the Solidity compiler version to 0.8.x or later. This would allow for the removal of SafeMath (as arithmetic operations would revert on overflow/underflow by default) and provide access to other modern language features and security improvements.


### `I-01` — Front-running Potential in EIP-712 Signature Functions  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). Functions like `permit` and `delegateBySig` allow users to perform gasless transactions by providing a signed message. While `nonces` and `deadlines` are correctly implemented to prevent replay attacks, these functions are still susceptible to front-running. A malicious actor could observe a pending signed transaction, submit it with a higher gas price, and potentially cause the original user's transaction to fail or incur unnecessary gas costs. This is a common characteristic of EIP-712 signature schemes and not a direct vulnerability in the contract's logic (7.2 Code Security).

**Recommendation:** Educate users about the potential for front-running when using signed messages for `permit` and `delegateBySig`. Advise them to use services that offer MEV protection or to be mindful of network congestion when submitting such transactions. No direct code change is required for this inherent characteristic.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x77fb...0ce0`](https://etherscan.io/address/0x77fba179c79de5b7653f68b5039af940ada60ce0) |
| **Network** | Ethereum |
| **Price** | $0.3369 |
| **24h Volume** | $318.6K |
| **Liquidity** | $454.4K |
| **Volume / Liquidity** | 0.7× |
| **Token Age** | 5y |
| **Top-10 Holders** | 69.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 255 buys / 367 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0xc1df8037881df17dc88998824b9aea81c71bbb1b)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/ampleforth-governance-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-13*
