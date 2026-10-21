---
token: FLOKI
ticker: FLOKI
network: ethereum
risk_score: 65
status: high
date: 2026-09-04
---

# FLOKI (FLOKI) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 65/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/floki-eth)

---

## Audit Summary

The FLOKI contract is an ERC-20 token with added governance delegation features, integrating with external Tax and Treasury handlers. The audit identified a critical vulnerability in the `transferFrom` function, allowing transfers without sufficient allowance, and a high-severity issue in the vote delegation logic that could lead to transaction reverts. Centralized control over critical external handlers by an EOA owner also presents a significant risk. The core `_transfer` function was not provided for review, limiting the scope of the audit.

> **Final Recommendation:** Address the critical `transferFrom` vulnerability immediately by reordering the allowance check and update before the actual token transfer. Rectify the vote tracking logic in `_moveDelegates` to prevent reverts and ensure consistent vote accounting. Consider implementing a multi-signature wallet for ownership to mitigate the risks associated with centralized control over critical external handlers and enhance operational security.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract implements ERC-20 and governance delegation, utilizing OpenZeppelin's Ownable for access control (7.2 Code Security, 7.3 Access Control). However, a critical flaw in `transferFrom`… |
| **Governance / Economics** | 2/10 | High | The token design includes a fixed total supply minted entirely to the deployer, which is a clear distribution strategy (7.4 Economic). The governance delegation mechanism is based on a standard… |
| **Upgrades** | 6/10 | Medium | The contract is not designed as an upgradeable proxy (7.7 Upgrades). This eliminates upgrade-related risks such as proxy misconfigurations or logic contract vulnerabilities during upgrades. However… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Locked** | 78.9% — UNCX |
| **Top-1 Unlocked Holder** | 12.5% |
| **Top-3 Unlocked** | 21.1% |
| **Lock Expiry** | ✅ 2286 (verified ≥ 1 year) — UNCX V2 |

## Security Findings

_🔴 1 Critical · 🟠 2 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 2 Informational_

### `C-01` — `transferFrom` Logic Flaw Allows Unauthorized Transfers  *(Severity: Critical · Status: Unresolved)*

The `transferFrom` function calls `_transfer(sender, recipient, amount)` *before* checking if `currentAllowance >= amount` and updating the allowance. This means tokens are transferred even if the allowance is insufficient, and then the transaction will revert on the `require` statement, but the tokens have already been moved. This allows an attacker to bypass allowance restrictions and transfer tokens without proper authorization, potentially draining funds from approved accounts.

**Recommendation:** Reorder the operations within `transferFrom`. The allowance check (`require(currentAllowance >= amount)`) and allowance update (`_approve(sender, _msgSender(), currentAllowance - amount)`) must occur *before* the `_transfer(sender, recipient, amount)` call.


### `H-01` — Vote Tracking Inconsistency and Potential Reverts in `_moveDelegates`  *(Severity: High · Status: Unresolved)*

The `_moveDelegates` function subtracts `amount` (which is `uint224(delegatorBalance)`) from the `from` delegate's vote count (`fromRepOld`). If `fromRepOld` is less than `amount`, this operation will cause an underflow and revert the transaction. This can occur if a delegator's balance changes (e.g., they transfer tokens) without their delegate's vote count being immediately adjusted, or if the `from` delegate has other delegators whose votes are not correctly accounted for in this specific operation. This can lead to a denial of service for delegation changes, hindering the governance mechanism.

**Recommendation:** Ensure that `fromRepOld` is always greater than or equal to `amount` before subtraction. This might require a more robust mechanism for tracking and updating delegate vote counts, possibly by adjusting votes based on actual token balance changes or by ensuring `fromRepOld` accurately reflects the delegator's contribution being moved. Consider adding a `require` statement to explicitly check `fromRepOld >= amount` before subtraction.


### `H-02` — Centralized Control Over Critical External Handlers  *(Severity: High · Status: Unresolved)*

The `owner` address has the exclusive privilege to call `setTaxHandler` and `setTreasuryHandler`, allowing them to change the addresses of `ITaxHandler` and `ITreasuryHandler` to any arbitrary contract. If the owner's private key is compromised or acts maliciously, they could replace these handlers with contracts designed to drain funds, impose exorbitant taxes, or otherwise disrupt token functionality, leading to significant financial loss for users.

**Recommendation:** Implement a more decentralized or time-locked mechanism for changing critical external handler addresses. This could involve a multi-signature wallet for ownership, a timelock contract, or a community governance vote to approve such changes. This reduces the risk associated with a single point of failure.


### `M-01` — Missing `_transfer` Function Implementation  *(Severity: Medium · Status: Unresolved)*

The provided source code is truncated and does not include the implementation of the internal `_transfer` function. This function is fundamental to the core ERC-20 token logic, handling balance updates and event emissions. Without its full implementation, a comprehensive security assessment of token transfers, including potential reentrancy vectors, balance manipulation, or other vulnerabilities, cannot be performed.

**Recommendation:** Provide the complete source code for the `_transfer` function to allow for a thorough security review of the token's core transfer mechanism. Ensure it adheres to ERC-20 standards and best security practices, including checks for zero addresses, sufficient balances, and proper event emission.


### `L-01` — Owner as Externally Owned Account (EOA)  *(Severity: Low · Status: Unresolved)*

The contract owner is an Externally Owned Account (EOA). An EOA is controlled by a single private key, making it a single point of failure. If this private key is compromised, lost, or misused, an attacker could gain full control over the owner-privileged functions, including changing critical `taxHandler` and `treasuryHandler` addresses.

**Recommendation:** Consider transferring ownership to a multi-signature wallet (e.g., Gnosis Safe) or a robust governance contract. This distributes control, requires multiple approvals for sensitive operations, and significantly reduces the risk associated with a single point of failure.


### `I-01` — Fixed Total Supply Minted to Deployer  *(Severity: Informational · Status: Unresolved)*

In the constructor, the entire fixed `totalSupply` (1e13 * 1e9) is minted directly to the contract deployer (`_msgSender()`). This design choice means that all tokens are initially held by a single address, which then controls the initial distribution.

**Recommendation:** This is a design decision and not a vulnerability in itself. However, ensure that the distribution strategy from the deployer's address is transparent and aligns with the project's economic model and community expectations.


### `I-02` — Potential `uint32` Overflow in `_writeCheckpoint` (Extreme Unlikelihood)  *(Severity: Informational · Status: Unresolved)*

The `numCheckpoints[delegatee] = nCheckpoints + 1;` operation increments a `uint32` counter. While highly improbable, if a single delegatee were to accumulate `2^32 - 1` (approximately 4.2 billion) checkpoints, the next increment would cause a `uint32` overflow, leading to a transaction revert. This would effectively halt further vote delegation changes for that specific delegatee.

**Recommendation:** Given the extreme unlikelihood of this scenario, no immediate action is strictly necessary. However, for absolute robustness, consider using a larger integer type (e.g., `uint64`) for `numCheckpoints` if the project anticipates an exceptionally high number of delegation changes per delegatee over a very long period.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xcf0c...6a2e`](https://etherscan.io/address/0xcf0c122c6b73ff809c693db761e7baebe62b6a2e) |
| **Network** | Ethereum |
| **Price** | $0.00002622 |
| **24h Volume** | $158.0K |
| **Liquidity** | $7.69M |
| **Volume / Liquidity** | 0.0× |
| **Token Age** | 4y |
| **Top-10 Holders** | 69.6% of supply |
| **Buy / Sell Tax** | 0.3% / 0.3% |
| **24h Transactions** | 60 buys / 104 sells |

## Security Flags (4/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0xca7c2771d248dcbe09eabe0ce57a62e18da178c0)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/floki-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-04*
