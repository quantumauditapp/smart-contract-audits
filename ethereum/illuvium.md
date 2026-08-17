---
token: Illuvium
ticker: ILV
network: ethereum
risk_score: 62
status: high
date: 2026-08-17
---

# Illuvium (ILV) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 62/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/illuvium-eth)

---

## Audit Summary

This audit covers the IlluviumERC20 token contract. The contract implements a standard ERC-20 token with custom access control, feature flags, and voting power delegation. Key functionalities include minting, burning, transfers, and allowance management. A significant limitation of this audit is the absence of the `AccessControl.sol` base contract and truncated critical functions (`__moveVotingPower`, `getVotingPowerAt`), which prevents a complete security assessment of the access control and voting delegation mechanisms.

> **Final Recommendation:** To ensure the highest level of security and transparency, it is crucial to provide the complete source code for all imported and truncated contracts, especially `AccessControl.sol` and the full implementations of `__moveVotingPower` and `getVotingPowerAt`. A thorough review of these components is essential to verify the integrity of access control and voting delegation. Additionally, consider documenting the rationale behind the `uint192.max` `totalSupply` limit and educate users about the safer `increaseAllowance`/`decreaseAllowance` functions to mitigate known ERC-20 `approve` race conditions.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The IlluviumERC20 contract demonstrates good adherence to the ERC-20 standard, including proper event emissions and robust checks for common arithmetic overflows/underflows in `increaseAllowance` and… |
| **Governance / Economics** | 1/10 | High | The contract design incorporates a custom access control system with distinct roles such as `ROLE_TOKEN_CREATOR` and `ROLE_TOKEN_DESTROYER`, granting significant power over the token supply to… |
| **Upgrades** | 3/10 | High | The IlluviumERC20 contract is implemented as a standard, non-upgradeable token contract (7.7 Upgrades). It does not utilize any proxy patterns (e.g., UUPS, Transparent) or other upgrade mechanisms.… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | 38.9% |
| **Top-3 Unlocked** | ⚠️ 80.2% |

## Security Findings

_🟠 2 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `H-01` — Incomplete Access Control Implementation Details  *(Severity: High · Status: Unresolved)*

The `IlluviumERC20` contract imports `AccessControl.sol`, but the source code for this critical base contract was not provided. This prevents a full audit of how roles (e.g., `ROLE_TOKEN_CREATOR`, `ROLE_TOKEN_DESTROYER`) are assigned, revoked, and how features (e.g., `FEATURE_TRANSFERS`) are enabled or disabled. The security of core functions like `mint` and `burn` heavily relies on the correct and secure implementation of this access control system.

**Recommendation:** Provide the complete source code for the `AccessControl.sol` contract to allow for a comprehensive security review of the access control mechanisms. Ensure that role management functions are adequately protected and follow best practices for privilege separation.


### `H-02` — Truncated Critical Logic for Voting Power  *(Severity: High · Status: Unresolved)*

The functions `__moveVotingPower` (an internal function central to voting power updates) and `getVotingPowerAt` (a public view function) are truncated in the provided source code. This prevents a thorough security analysis of the voting power delegation mechanism, which is a significant feature of this token. Without the full implementation, potential vulnerabilities such as incorrect voting power calculations, manipulation, or denial-of-service attacks cannot be identified.

**Recommendation:** Provide the complete source code for `__moveVotingPower` and `getVotingPowerAt` to enable a full audit of the voting power delegation logic. Ensure that all calculations are correct, history is properly maintained, and potential edge cases are handled securely.


### `M-01` — Inconsistent Total Supply Limit  *(Severity: Medium · Status: Unresolved)*

The `mint` function includes a `require(totalSupply + _value <= type(uint192).max, "total supply overflow (uint192)");` check. While `totalSupply` is declared as `uint256`, its maximum value is explicitly limited to `type(uint192).max`. Individual `tokenBalances` are also `uint256`. This inconsistency in type declaration versus actual limit could lead to confusion or unexpected behavior if not clearly documented, potentially causing `mint` operations to fail prematurely even if `uint256` could accommodate larger values.

**Recommendation:** Clarify the design choice behind limiting `totalSupply` to `uint192.max` while using `uint256` for the variable itself and for `tokenBalances`. Consider if `totalSupply` should be `uint192` if this is the intended maximum, or if the limit should be removed if `uint256` capacity is desired. Ensure this design decision is well-documented.


### `L-01` — Standard ERC-20 `approve` Race Condition  *(Severity: Low · Status: Unresolved)*

The `approve` function is susceptible to a known front-running attack. If a user approves an allowance of `X` and then, before the first transaction is mined, sends another transaction to approve `Y`, a malicious actor could front-run the second transaction. This allows the attacker to spend `X` tokens, and then the second `approve` transaction for `Y` is mined, allowing the attacker to spend `Y` tokens, effectively spending `X + Y` instead of just `Y`.

**Recommendation:** While `increaseAllowance` and `decreaseAllowance` functions are provided to mitigate this, users should be educated to use these functions instead of directly calling `approve` when modifying an existing allowance. If `approve` must be used, the best practice is to first set the allowance to zero and wait for that transaction to confirm before setting a new allowance.


### `I-01` — Centralized Control over Token Supply and Features  *(Severity: Informational · Status: Unresolved)*

The contract design grants significant centralized control to addresses holding specific roles, such as `ROLE_TOKEN_CREATOR` (for minting tokens) and `ROLE_TOKEN_DESTROYER` (for burning tokens). Additionally, administrators can enable or disable core token features (e.g., transfers, burns) via feature flags. This level of centralization, while offering flexibility in managing the token, introduces a single point of failure and relies heavily on the trustworthiness and security practices of the entities controlling these roles.

**Recommendation:** Clearly document the roles, their associated privileges, and the process for assigning/revoking these roles. Consider implementing a multi-signature wallet or a decentralized governance mechanism for critical roles and feature management to reduce centralization risks over time.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x767f...ca0e`](https://etherscan.io/address/0x767fe9edc9e0df98e07454847909b5e959d7ca0e) |
| **Network** | Ethereum |
| **Price** | $3.0270 |
| **24h Volume** | $64.7K |
| **Liquidity** | $1.68M |
| **Volume / Liquidity** | 0.0× |
| **Token Age** | 5y |
| **Top-10 Holders** | 61.3% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 110 buys / 146 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x6a091a3406e0073c3cd6340122143009adac0eda)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/illuvium-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-17*
