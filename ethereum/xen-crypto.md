---
token: XEN Crypto
ticker: XEN
network: ethereum
risk_score: 11
status: low
date: 2026-09-04
---

# XEN Crypto (XEN) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 11/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/xen-crypto-eth)

---

## Audit Summary

The audit focused on the `Math` library, which serves as an implementation for the XENCrypto proxy. The `Math` contract provides basic utility functions and leverages the well-established `ABDKMath64x64` library for fixed-point arithmetic. The contract is stateless and contains no complex logic, access control, or economic mechanisms. The `ABDKMath64x64` library employs robust checks to prevent common fixed-point arithmetic issues. Overall, the technical risk is low due to the simplicity and reliance on a battle-tested library.

> **Final Recommendation:** The `Math` contract is a well-structured and secure implementation for fixed-point arithmetic, leveraging a reputable third-party library. It is recommended to ensure that the complete `ABDKMath64x64` library, including the truncated `log_2` function, has undergone thorough review. For any future upgrades, maintain the stateless and pure nature of the implementation to preserve its low-risk profile.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The `Math` contract (7.1 Architecture) is a simple, stateless library providing `min`, `max`, and `logX64` functions. Its core functionality for fixed-point arithmetic is delegated to the… |
| **Governance / Economics** | 3/10 | High | The `Math` contract is a pure utility library (7.4 Economic). It does not manage any assets, tokens, or user funds, nor does it implement any economic models or fee structures. Consequently, there… |
| **Upgrades** | 6/10 | Medium | The `Math` contract serves as an implementation behind a proxy (7.7 Upgrades). As a stateless and pure library, it is an ideal candidate for an upgradeable implementation, minimizing upgrade-related… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 73.9% |
| **Top-3 Unlocked** | ⚠️ 92.8% |

## Security Findings

_🟢 1 Low · ⚪ 2 Informational_

### `L-01` — Extensive Use of `require` for Fixed-Point Range Checks  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `ABDKMath64x64` library extensively uses `require` statements within `unchecked` blocks to enforce range limits (`MIN_64x64`, `MAX_64x64`) for 64.64-bit fixed-point numbers after intermediate `int256` calculations. While these checks are crucial for preventing overflows/underflows and ensuring mathematical correctness, they can lead to higher gas costs for transactions that provide inputs resulting in out-of-range fixed-point values, as such transactions will revert. This is an expected trade-off for safety in fixed-point arithmetic.

**Recommendation:** This is a design choice for safety and is generally acceptable for fixed-point libraries. Users of the `Math` library should be aware that inputs leading to results outside the 64.64-bit range will cause transactions to revert. No direct action is required unless gas optimization for invalid inputs is a critical concern, which would typically involve a different fixed-point implementation strategy.


### `I-01` — Reliance on Third-Party Library  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `Math` contract's core functionality for fixed-point arithmetic is entirely dependent on the `ABDKMath64x64` library. While `ABDKMath64x64` is a well-known and generally robust library, any undiscovered vulnerability or subtle bug within its extensive codebase would directly impact the `Math` contract and any protocol relying on it. This introduces an inherent dependency risk.

**Recommendation:** Ensure that the `ABDKMath64x64` library has been thoroughly audited independently and that its specific version used in this project is free from known vulnerabilities. Consider maintaining a local copy of the audited version to prevent unexpected changes from external dependencies.


### `I-02` — Truncated `log_2` Function in `ABDKMath64x64`  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The provided source code for the `ABDKMath64x64.log_2` function is incomplete, indicated by `... (truncated)`. Without the full implementation, a comprehensive security assessment of this specific function's logic, including potential edge cases, gas consumption, and correctness, cannot be performed.

**Recommendation:** Provide the complete source code for the `ABDKMath64x64.log_2` function to allow for a full and thorough audit of its implementation. Verify that the deployed bytecode matches the complete source code.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x0645...6fb8`](https://etherscan.io/address/0x06450dee7fd2fb8e39061434babcfc05599a6fb8) |
| **Network** | Ethereum |
| **Price** | $0. |
| **24h Volume** | $49.1K |
| **Liquidity** | $57.7K |
| **Volume / Liquidity** | 0.9× |
| **Token Age** | 3y |
| **Top-10 Holders** | 18.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 97 buys / 62 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x2a9d2ba41aba912316d16742f259412b681898db)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/xen-crypto-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-04*
