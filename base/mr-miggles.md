---
token: Mr. Miggles
ticker: MIGGLES
network: base
risk_score: 0
status: low
date: 2026-08-17
---

# Mr. Miggles (MIGGLES) — Smart Contract Security Analysis | Base

> **Risk Score: 0/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/mr-miggles-base)

---

## Audit Summary

The Erc20 token contract implements a standard ERC-20 interface with an Ownable access control pattern. It includes a unique 'launched' state mechanism that restricts transfers to/from contracts before launch, providing a controlled distribution phase. The contract utilizes Solidity 0.8.24, benefiting from built-in overflow/underflow protections. Identified issues primarily relate to the implications of the pre-launch transfer restrictions and a non-standard self-transfer prohibition.

> **Final Recommendation:** It is recommended to thoroughly document the pre-launch transfer restrictions and the self-transfer prohibition to ensure all users and integrating protocols are aware of these non-standard behaviors. Consider emitting an event when the `launch()` function is called to provide better off-chain monitoring capabilities. Review the necessity of disallowing self-transfers to maintain broader ERC-20 compatibility.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 9/10 | Low | The contract is written in Solidity 0.8.24, which includes built-in overflow/underflow checks, enhancing code security (7.2 Code Security). It uses the Address library for safe low-level calls. A key… |
| **Governance / Economics** | 9/10 | Low | The contract employs the Ownable pattern, granting the deployer significant control, particularly over the 'launch' function (7.3 Access Control). Before the token is 'launched', transfers to or from… |
| **Upgrades** | 10/10 | Low | The contract is not designed to be upgradeable; it does not implement any proxy patterns (7.7 Upgrades). This eliminates risks associated with upgrade mechanisms, such as proxy misconfigurations or… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% |

## Security Findings

_🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `H-01` — Centralized Control and Pre-Launch Transfer Restrictions  *(Severity: High · Status: Unresolved)*

The `Erc20` contract implements a `launched` state, controlled by the `onlyOwner` function `launch()`. Before `launched` is true, the `_transferAllowed` function prevents transfers to or from any contract address (`from.isContract() \|\| to.isContract()`). This mechanism, while potentially intended to prevent sniping or control initial distribution, significantly centralizes control in the owner's hands and can block legitimate interactions with DEXes, aggregators, multisigs, or other DeFi protocols until the owner calls `launch()`. The `transferFrom` function also includes a special path allowing the owner to move tokens from an approved address to themselves before launch, further highlight…

**Recommendation:** Ensure comprehensive documentation clearly outlines the pre-launch phase, its implications for token holders, and how it affects interactions with other smart contracts. Consider if the `isContract()` check is overly restrictive; if specific contract types (e.g., known DEX routers) are intended to be allowed, a whitelist mechanism could be explored. Communicate the owner's role and the timing of the `launch()` function transparently.


### `M-01` — Non-Standard Self-Transfer Restriction  *(Severity: Medium · Status: Unresolved)*

The `_transfer` function includes a `require(from != to, "you cannot transfer to yourself");` check. While seemingly a minor restriction, standard ERC-20 implementations typically allow transfers from an address to itself. Some protocols, dApps, or internal accounting systems might expect or rely on the ability to perform self-transfers for various reasons, such as gas optimization or re-triggering hooks. This deviation from the ERC-20 standard could lead to unexpected reverts or integration issues.

**Recommendation:** Consider removing the `require(from != to, "you cannot transfer to yourself");` check to align with standard ERC-20 behavior and improve compatibility with existing infrastructure. If this restriction is intentional, thoroughly document its purpose and potential implications for users and integrators.


### `L-01` — Missing Event for `launch()` Function  *(Severity: Low · Status: Unresolved)*

The `launch()` function, which transitions the token from a restricted pre-launch state to a fully transferable state, does not emit an event upon successful execution. This makes it challenging for off-chain systems, such as block explorers, dApps, and analytics tools, to programmatically monitor the token's launch status and react accordingly without constantly polling the `launched` state variable.

**Recommendation:** Emit an event (e.g., `event Launched(address indexed caller, uint256 timestamp);`) when the `launch()` function is successfully called. This provides a clear, auditable, and easily monitorable signal for off-chain services.


### `I-01` — Assembly Usage in `_revert` Function  *(Severity: Informational · Status: Unresolved)*

The `_revert` function within the `Address` library uses inline assembly to handle reverts with custom error data. While this approach is functional and can be efficient for forwarding raw revert data, direct assembly usage can sometimes reduce code readability and increase the potential for subtle errors compared to higher-level Solidity constructs. In Solidity 0.8.x, `abi.decode` and `revert` can often achieve similar results for string error messages.

**Recommendation:** Review if the assembly usage in `_revert` is strictly necessary for its intended purpose. If a more idiomatic Solidity approach can achieve the same functionality with improved readability and maintainability, consider refactoring. However, for a utility library function designed for precise error forwarding, the current implementation may be acceptable.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xb1a0...f25d`](https://basescan.org/address/0xb1a03eda10342529bbf8eb700a06c60441fef25d) |
| **Network** | Base |
| **Price** | $0.001714 |
| **24h Volume** | $107.2K |
| **Liquidity** | $342.4K |
| **Volume / Liquidity** | 0.3× |
| **Token Age** | 2y |
| **Top-10 Holders** | 24.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 397 buys / 283 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0x17a3ad8c74c4947005afeda9965305ae2eb2518a)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/mr-miggles-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-17*
