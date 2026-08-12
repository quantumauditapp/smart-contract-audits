---
token: MatthewCoin
ticker: MATTHEWCOIN
network: bsc
risk_score: 23
status: medium
date: 2026-08-12
---

# MatthewCoin (MATTHEWCOIN) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 23/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/matthewcoin-bsc)

---

## Audit Summary

This audit covers the `Address.sol` utility library from OpenZeppelin Contracts. This library provides essential low-level address interaction functions, including safe ETH transfers and robust wrappers for `call`, `delegatecall`, and `staticcall`. As a widely used and thoroughly audited component of the OpenZeppelin suite, the contract itself exhibits high security standards and best practices. The identified findings are informational, highlighting common pitfalls and security considerations for developers integrating this library into their own contracts, rather than vulnerabilities within the library itself.

> **Final Recommendation:** The `Address.sol` library is a robust and well-audited component. Developers integrating this library should carefully review the explicit warnings within its documentation regarding potential misuse, particularly concerning reentrancy and the limitations of `isContract`. Always follow the checks-effects-interactions pattern when performing external calls, even when using the library's safe wrappers. Ensure that any contract utilizing these low-level call functions properly handles return values and potential reverts to maintain overall system security.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The `Address` library (7.1 Architecture) is a foundational utility from OpenZeppelin, designed to provide safer interactions with addresses and low-level calls. It includes functions like `sendValue`… |
| **Governance / Economics** | 5/10 | Medium | This contract is a utility library and does not implement any specific governance mechanisms (7.5 Governance) or economic models (7.4 Economic). Therefore, governance and economic risks are not… |
| **Upgrades** | 9/10 | Low | As a Solidity library, `Address.sol` is typically deployed as immutable bytecode and linked at compile time or used via `delegatecall` in proxy patterns. It is not designed for direct upgradeability… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_⚪ 3 Informational_

### `I-01` — Misuse of `isContract` for Security Checks  *(Severity: Informational · Status: Unresolved)*

The `isContract` function, while useful, has limitations explicitly noted in its documentation. It is unsafe to assume that an address for which this function returns `false` is an externally-owned account (EOA). Furthermore, `isContract` should not be relied upon to protect against flash loan attacks or to prevent calls from contracts, as it can be circumvented (e.g., by calling from a contract constructor). This is a common misunderstanding that can lead to access control bypasses or unexpected behavior (7.2 Code Security, 7.3 Access Control).

**Recommendation:** Avoid using `isContract` as a primary security mechanism to distinguish between EOAs and contracts, or to prevent flash loan attacks. Instead, implement robust access control mechanisms (e.g., `Ownable`, role-based access control) and reentrancy guards where necessary. If distinguishing between EOAs and contracts is critical, consider alternative, more robust methods or acknowledge the inherent limitations.


### `I-02` — Reentrancy Risk with External ETH Transfers  *(Severity: Informational · Status: Unresolved)*

The `sendValue` function, while a safer alternative to `transfer`, explicitly warns that 'control is transferred to `recipient`, care must be taken to not create reentrancy vulnerabilities.' This highlights a critical security consideration for any contract performing external ETH transfers. If the recipient is a malicious contract, it can re-enter the calling contract before its state is updated, leading to potential fund drains (7.2 Code Security).

**Recommendation:** Always adhere to the 'checks-effects-interactions' pattern when performing external calls, especially those involving value transfers. Update all relevant state variables *before* initiating any external calls. Consider using a reentrancy guard (e.g., OpenZeppelin's `ReentrancyGuard`) for functions that perform external calls and modify critical state.


### `I-03` — Risks Associated with Low-Level Calls  *(Severity: Informational · Status: Unresolved)*

The library provides wrappers for low-level `call`, `delegatecall`, and `staticcall` functions (e.g., `functionCallWithValue`, `functionDelegateCall`). While these wrappers include important safety checks (like `success` verification and error bubbling), the inherent risks of low-level calls remain. Incorrect `data` parameters, calls to untrusted contracts, or unexpected re-entrancy from the called contract can lead to vulnerabilities, even with these wrappers. `delegatecall` is particularly powerful and risky, as it executes code in the context of the calling contract (7.2 Code Security, 7.6 External).

**Recommendation:** Exercise extreme caution when using low-level call functions. Ensure that the target address is trusted and that the `data` payload is correctly formatted and validated. For `delegatecall`, only use it with trusted, audited implementation contracts. Implement robust error handling and consider the potential for reentrancy or unexpected state changes in the calling contract due to external interactions.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xad5b...ffff`](https://bscscan.com/address/0xad5b3485a44d2241998a0d86ea395c8f4a51ffff) |
| **Network** | BNB Chain |
| **Price** | $0.00003023 |
| **24h Volume** | $106.8K |
| **Liquidity** | $19.4K |
| **Volume / Liquidity** | 5.5× |
| **Token Age** | 1d |
| **Top-10 Holders** | 50.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 758 buys / 631 sells |

## Security Flags (4/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x429d4b3356ba0a8e1780106c00346916ee9891b1)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/matthewcoin-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-12*
