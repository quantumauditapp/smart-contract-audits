---
token: Lido DAO
ticker: LDO
network: ethereum
risk_score: 58
status: high
date: 2026-07-16
---

# Lido DAO (LDO) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 58/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/lido-dao-eth)

---

## Audit Summary

The MiniMeToken contract implements an ERC20-like token with a unique cloning mechanism and a controller pattern. The audit identified significant centralization risks due to the extensive powers of the `controller` address. Additionally, the use of an outdated Solidity compiler version (0.4.24) introduces potential vulnerabilities related to integer arithmetic and known compiler bugs. While the contract provides core token functionality, several aspects deviate from modern security best practices, warranting careful review and potential upgrades.

> **Final Recommendation:** It is strongly recommended to migrate to a more modern Solidity compiler version (e.g., 0.8.x) and incorporate robust security libraries like OpenZeppelin Contracts, especially for arithmetic operations (SafeMath). The extensive centralized control by the `controller` should be carefully evaluated; if decentralization is a goal, consider implementing a multi-signature wallet or a robust governance mechanism for critical functions. Additionally, ensure all critical state-changing actions emit events for transparency and off-chain monitoring.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract implements a custom ERC20-like token with a historical balance tracking mechanism. Strengths include a clear separation of concerns with the `Controlled` base contract and an… |
| **Governance / Economics** | 1/10 | High | The economic and governance model is highly centralized around the `controller` address. This address, initially the contract deployer, has extensive power, including the ability to change the… |
| **Upgrades** | 5/10 | Medium | The MiniMeToken contract is not designed as an upgradeable proxy contract. It is a standard, immutable contract deployed directly to the blockchain. Therefore, there are no upgrade-specific risks… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | 25.1% |
| **Top-3 Unlocked** | 54.2% |

## Security Findings

_🟠 1 High · 🟡 2 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `H-01` — Centralized Control by Controller  *(Severity: High · Status: Unresolved)*

The `controller` address, initially the contract deployer, possesses extensive power over the token contract. This includes the ability to change the controller, enable/disable transfers, and bypass standard `transferFrom` allowance checks to move tokens arbitrarily. This represents a significant centralization risk and a single point of failure. If the controller's private key is compromised, all token holders could be at risk.

**Recommendation:** Evaluate if such a high degree of centralization is necessary. If not, consider implementing a multi-signature wallet for the controller address or transitioning control to a decentralized autonomous organization (DAO) for critical functions like `changeController` and `enableTransfers`/`disableTransfers`. Ensure robust security measures are in place for the controller's private key.


### `M-01` — Old Solidity Compiler Version and Lack of SafeMath  *(Severity: Medium · Status: Unresolved)*

The contract uses `pragma solidity ^0.4.24`, an outdated compiler version. This version lacks built-in overflow/underflow protection (like SafeMath in newer versions) and may contain known compiler bugs. While some checks are present (e.g., `previousBalanceFrom >= _amount`), other arithmetic operations, especially with `uint128` values in `Checkpoint` structs or in the truncated `generateTokens`/`destroyTokens` functions, could be vulnerable if not explicitly guarded. This increases the risk of unexpected behavior or exploits.

**Recommendation:** Upgrade the contract to a modern Solidity compiler version (e.g., 0.8.x) which includes default overflow/underflow checks. If upgrading is not feasible, thoroughly audit all arithmetic operations, especially those involving `uint128` and `uint256` types, and explicitly implement `SafeMath` checks for all additions, subtractions, and multiplications to prevent overflows and underflows.


### `M-02` — ERC20 `approve` Front-Running Vulnerability  *(Severity: Medium · Status: Unresolved)*

The standard ERC20 `approve` function is susceptible to a known front-running attack. If a user approves an amount, then attempts to approve a different amount, a malicious actor can front-run the second transaction. This allows the malicious actor to spend the original approved amount, and then the new approval is set, potentially leading to a double-spend of the approved amount if the user intended to reduce the allowance.

**Recommendation:** Advise users to set the allowance to zero (`approve(spender, 0)`) before setting a new non-zero allowance. Alternatively, consider implementing an `increaseAllowance` and `decreaseAllowance` pattern, as seen in modern ERC20 implementations, which mitigates this specific front-running vector.


### `L-01` — Non-Standard `transferFrom` Return Behavior  *(Severity: Low · Status: Unresolved)*

The `transferFrom` function returns `false` on insufficient allowance rather than reverting. While technically compliant with the original ERC20 specification, modern Solidity best practices and many integrations expect a `revert` on failure. Returning `false` can lead to unexpected behavior or silent failures in consuming contracts that do not explicitly check the return value.

**Recommendation:** Consider modifying the `transferFrom` function to `revert` (using `require()` or `revert()`) instead of returning `false` when the allowance is insufficient. This aligns with current best practices and improves compatibility with modern DeFi protocols and tools.


### `I-01` — Lack of Event Emission for Critical Actions  *(Severity: Informational · Status: Unresolved)*

Critical state-changing actions, such as `changeController`, `enableTransfers`, `disableTransfers`, and potentially token minting/burning (if present in the truncated code), do not emit corresponding events. This hinders off-chain monitoring, transparency, and makes it difficult to track significant administrative changes or token supply adjustments.

**Recommendation:** Emit events for all critical state-changing functions. For example, `event ControllerChanged(address indexed oldController, address indexed newController);` or `event TransfersEnabled(bool enabled);`. This enhances transparency and allows for easier integration with off-chain monitoring systems.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x5a98...1b32`](https://etherscan.io/address/0x5a98fcbea516cf06857215779fd812ca3bef1b32) |
| **Network** | Ethereum |
| **Price** | $0.3648 |
| **24h Volume** | $253.5K |
| **Liquidity** | $558.1K |
| **Volume / Liquidity** | 0.5× |
| **Token Age** | 5y |
| **Top-10 Holders** | 49.3% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 227 buys / 186 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0xa3f558aebaecaf0e11ca4b2199cc5ed341edfd74)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/lido-dao-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-07-16*
