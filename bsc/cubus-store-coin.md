---
token: Cubus Store Coin
ticker: CSC
network: bsc
risk_score: 17
status: low
date: 2026-08-12
---

# Cubus Store Coin (CSC) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 17/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/cubus-store-coin-bsc)

---

## Audit Summary

This audit covers the OpenZeppelin `Address` utility library. The library itself is a widely used and thoroughly audited component, providing safe wrappers for low-level address operations. The identified findings are primarily informational, highlighting important considerations and warnings explicitly documented within the library for its safe and secure integration into other contracts.

> **Final Recommendation:** While the OpenZeppelin `Address` library itself is highly secure, its safe usage depends on the calling contract's implementation. Developers integrating this library should meticulously review the explicit warnings provided in the NatSpec comments, particularly concerning the limitations of `isContract` and the reentrancy risks associated with external calls like `sendValue` and `functionCallWithValue`.

Always apply the checks-effects-interactions pattern, utilize reentrancy guards where necessary, and thoroughly validate inputs and outputs for any external interactions facilitated by this library to ensure overall system security.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The `Address` library (7.1 Architecture) is a robust and well-tested utility from OpenZeppelin, designed to provide safer interactions with addresses and low-level calls. It includes functions like… |
| **Governance / Economics** | 6/10 | Medium | The `Address` library is a foundational utility and does not incorporate any specific governance or economic mechanisms (7.4 Economic, 7.5 Governance). Its design is purely functional, providing… |
| **Upgrades** | 10/10 | Low | As a Solidity library, `Address` is not designed to be an upgradeable contract (7.7 Upgrades). It is typically linked or embedded into other contracts at deployment. This design inherently avoids… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | 47.0% |
| **LP Locked** | 47.0% — Null Address |
| **Top-1 Unlocked Holder** | 26.0% |
| **Top-3 Unlocked** | 52.9% |

## Security Findings

_⚪ 3 Informational_

### `I-01` — Limitations of `isContract` for Security Checks  *(Severity: Informational · Status: Unresolved)*

The `isContract` function, while useful for certain checks, has known limitations and is explicitly warned against being used for security-critical checks, especially to prevent flash loan attacks or to reliably distinguish between Externally Owned Accounts (EOAs) and contracts. It returns `false` for contracts in construction, destroyed contracts, or addresses where a contract will be created, making it unreliable for strict access control or attack prevention.

**Recommendation:** Developers should not rely on `isContract` as a primary security mechanism to prevent calls from contracts or to protect against flash loan attacks. Instead, robust access control mechanisms (e.g., `Ownable`, `AccessControl`), reentrancy guards, and careful state management should be employed for security-sensitive operations.


### `I-02` — Reentrancy Risk with External Calls (sendValue)  *(Severity: Informational · Status: Unresolved)*

The `sendValue` function, which uses a low-level `call` to transfer Ether, explicitly warns about the potential for reentrancy vulnerabilities if not handled correctly by the calling contract. While `sendValue` itself uses `require` before the call (adhering to checks-effects-interactions for its own balance), the recipient can still re-enter the *calling* contract, potentially leading to unexpected behavior or fund drains.

**Recommendation:** Any contract utilizing `sendValue` or other external call functions must strictly adhere to the checks-effects-interactions pattern. Implement reentrancy guards (e.g., OpenZeppelin's `ReentrancyGuard`) on functions that perform external calls and modify state, especially when handling Ether or tokens, to prevent malicious re-entry.


### `I-03` — Safe Usage of Low-Level Call Wrappers  *(Severity: Informational · Status: Unresolved)*

The `Address` library provides several wrappers for low-level calls (`functionCall`, `functionCallWithValue`, `functionStaticCall`, `functionDelegateCall`). While these wrappers improve safety by handling error propagation and checking for contract existence (in `verifyCallResultFromTarget`), they still transfer control to an external address. Improper use by the calling contract can lead to unexpected behavior, gas limit issues, or reentrancy.

**Recommendation:** When using these low-level call wrappers, developers must ensure that the target contract's behavior is well-understood and trusted. Implement robust input validation, handle potential reverts gracefully, and be mindful of gas limits and reentrancy risks, especially with `functionCallWithValue` and `functionDelegateCall` which involve value transfers or delegate logic execution.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x0296...ffff`](https://bscscan.com/address/0x02962e4188902e05c4b1856e065551bcce10ffff) |
| **Network** | BNB Chain |
| **Price** | $0.01676 |
| **24h Volume** | $197.4K |
| **Liquidity** | $822.8K |
| **Volume / Liquidity** | 0.2× |
| **Token Age** | 24d |
| **Top-10 Holders** | 197.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1496 buys / 405 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xf55c23a434426b985d512e2e5519114a5d0249b6)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/cubus-store-coin-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-12*
