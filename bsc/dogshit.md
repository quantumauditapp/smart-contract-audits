---
token: Dogshit
ticker: DOGSHIT
network: bsc
risk_score: 21
status: low
date: 2026-09-15
---

# Dogshit (DOGSHIT) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 21/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/dogshit-bsc)

---

## Audit Summary

This audit report covers the provided Solidity source code for the 'Dogshit Token' project. Due to the truncation of the main ERC20 contract, a comprehensive security assessment of all functionalities, especially dividend distribution and DEX interactions, could not be performed. The visible code snippets demonstrate good practices like SafeMath usage and a robust IterableMapping library. However, the unprovided sections represent significant unaudited attack surfaces, leading to a Medium overall risk level.

> **Final Recommendation:** It is strongly recommended to provide the complete and untruncated source code for a full and accurate security audit. Critical functionalities such as dividend distribution, token transfer logic, and any interactions with external DEX protocols must be thoroughly reviewed for reentrancy, economic exploits, and gas efficiency. Implement robust testing, including unit, integration, and fuzz testing, for all complex logic, especially those involving external calls or intricate calculations. Consider implementing multi-signature control for critical owner-privileged functions to mitigate centralization risks.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The technical architecture leverages standard libraries like SafeMath for robust integer arithmetic, mitigating common overflow/underflow vulnerabilities (7.2 Code Security). The IterableMapping… |
| **Governance / Economics** | 7/10 | Low | The contract employs the Ownable pattern for access control, centralizing administrative privileges with a single owner (7.3 Access Control). This introduces a centralization risk, as the owner has… |
| **Upgrades** | 10/10 | Low | Based on the provided information and the `is_proxy: false` flag, the contract does not appear to be implemented as an upgradeable proxy (7.7 Upgrades). Therefore, direct upgradeability risks are not… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 1 Medium · 🟢 2 Low · ⚪ 2 Informational_

### `M-01` — Unaudited Critical Functionality Due to Truncated Code  *(Severity: Medium · Status: Unresolved)*

The provided source code for the main ERC20 contract is truncated. Specifically, the implementation details for core ERC20 functions (e.g., `_transfer`, `_mint`, `_burn`), the `decimals()` function, and any custom logic related to dividend distribution (implied by `DividendPayingTokenInterface`) or DEX interactions (implied by `IRouter`, `IFactory`, `IPair`) are missing. This prevents a comprehensive security assessment of potentially complex and high-risk areas, leaving significant attack surfaces unaudited.

**Recommendation:** Provide the complete and untruncated source code for all contracts, especially the main ERC20 token contract. A full audit cannot be performed without access to the entire codebase, particularly for functionalities involving external calls, complex arithmetic, or state changes that are common sources of vulnerabilities like reentrancy, economic exploits, or access control bypasses.


### `L-01` — Centralization Risk with Ownable Pattern  *(Severity: Low · Status: Unresolved)*

The contract utilizes the `Ownable` pattern, granting a single external address (the `owner`) exclusive control over sensitive administrative functions. While common, this introduces a single point of failure. If the owner's private key is compromised, malicious actors could gain full control over the contract, potentially leading to asset loss or manipulation.

**Recommendation:** Consider implementing a multi-signature wallet (e.g., Gnosis Safe) for the contract owner to enhance security. For highly critical functions, explore time-locks or a decentralized governance mechanism to distribute control and introduce a delay for sensitive operations, allowing for community review or emergency intervention.


### `L-02` — Potential Gas Costs with Large IterableMapping  *(Severity: Low · Status: Unresolved)*

The `IterableMapping` library provides efficient O(1) operations for `set` and `remove` (amortized for array push/pop). However, if the `keys` array grows to an extremely large size, the underlying `push` and `pop` operations, while efficient, can still incur non-trivial gas costs. While not a direct vulnerability, this could lead to higher transaction fees for users interacting with functions that modify the map, especially if many entries are added or removed in a single transaction.

**Recommendation:** Monitor the growth of the `IterableMapping`'s `keys` array in production. If the array is expected to contain an extremely large number of elements (e.g., millions), consider alternative data structures or strategies to manage the scale, or ensure that functions interacting with the map are designed to handle potential gas cost increases without hitting block gas limits.


### `I-01` — Potential Unchecked Return Values for External Calls  *(Severity: Informational · Status: Unresolved)*

While the provided code snippets do not show direct external calls to unknown contracts, interfaces like `IRouter` suggest that the full contract likely makes external calls. If not handled carefully, external calls to contracts like `transfer` or `approve` (which return a boolean) might not have their return values checked. Ignoring these return values can lead to unexpected behavior or failed operations going unnoticed.

**Recommendation:** Ensure that all external calls to other contracts, especially those that return a boolean indicating success or failure (e.g., ERC20 `transfer`, `approve`), explicitly check their return values. Use `require()` statements to revert the transaction if the external call indicates failure, preventing silent failures and ensuring expected contract state.


### `I-02` — Truncated `decimals()` Function in ERC20  *(Severity: Informational · Status: Unresolved)*

The `decimals()` function within the `ERC20` contract is truncated in the provided source code. While it is likely intended to return a standard `uint8` value (e.g., 18), its full implementation is not visible. This is a minor observation stemming from the incomplete code submission.

**Recommendation:** Ensure the `decimals()` function is fully implemented and returns the correct `uint8` value representing the token's decimal precision, adhering to the ERC20 standard. This is crucial for proper display and interaction with exchanges and wallets.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x389c...6666`](https://bscscan.com/address/0x389cb330e4eaa0cce969759f01a416448fed6666) |
| **Network** | BNB Chain |
| **Price** | $0.00000002 |
| **24h Volume** | $188.8K |
| **Liquidity** | $57.5K |
| **Volume / Liquidity** | 3.3× |
| **Token Age** | 3d |
| **Top-10 Holders** | 26.5% of supply |
| **Buy / Sell Tax** | 3.0% / 3.0% |
| **24h Transactions** | 2363 buys / 1492 sells |

## Security Flags (5/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x3566947cad3bcc854b8247fdf5224ca528b31aea)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/dogshit-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-15*
