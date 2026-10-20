---
token: Paimon Polymarket SPV Token
ticker: PPOLY
network: bsc
risk_score: 45
status: medium
date: 2026-09-25
---

# Paimon Polymarket SPV Token (PPOLY) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 45/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/paimon-polymarket-spv-token-bsc)

---

## Audit Summary

The PreIPOToken contract implements a standard ERC-20 token with Pausable functionality, largely following OpenZeppelin patterns. The contract is well-structured and utilizes recent Solidity features like custom errors and `unchecked` blocks for gas optimization where safe. Key functionalities like minting, burning, and pausing are implemented as internal functions, implying a fixed supply and non-pausable token unless a derived contract exposes these with appropriate access control. The overall risk is assessed as Low due to the contract's simplicity and adherence to established patterns, with minor informational findings.

> **Final Recommendation:** It is recommended to clearly document the intended immutability and fixed supply nature of the token, especially regarding the internal-only `_mint`, `_burn`, `_pause`, and `_unpause` functions. If any of these functionalities are intended to be externally callable, a derived contract should be implemented with appropriate access control (e.g., `onlyOwner` or multi-sig). Additionally, consider removing the unused `SafeIntrospection` library to reduce bytecode size and complexity.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract demonstrates good technical architecture (7.1) by inheriting from well-audited OpenZeppelin-like ERC20 and Pausable base contracts. Code security (7.2) is strong, utilizing Solidity… |
| **Governance / Economics** | 2/10 | High | The economic model (7.4) for PreIPOToken appears to be a fixed-supply token, as `_mint` and `_burn` functions are internal and not exposed externally. This design choice simplifies the economic… |
| **Upgrades** | 3/10 | High | The PreIPOToken contract is not designed as an upgradeable proxy (7.7). It is an immutable contract, meaning its logic cannot be changed after deployment. This design choice eliminates… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 94.9% |
| **Top-3 Unlocked** | ⚠️ 97.9% |

## Security Findings

_🟢 1 Low · ⚪ 2 Informational_

### `L-01` — Missing External Access Control for Core Functions  *(Severity: Low · Status: Unresolved)*

The `_mint`, `_burn`, `_pause`, and `_unpause` functions are implemented as `internal virtual`. This means that the `PreIPOToken` contract itself does not expose these functionalities externally. If the intention is for the token supply to be mutable or for the token to be pausable, a derived contract must implement external functions with appropriate access control (e.g., `onlyOwner` or a multi-sig mechanism) to call these internal functions. Without such external wrappers, the token's supply is fixed after initial deployment (if `_mint` is called in constructor) and the pausing mechanism is unusable.

**Recommendation:** If minting, burning, or pausing capabilities are desired, implement a derived contract that exposes these functionalities via external functions, protected by robust access control mechanisms (e.g., OpenZeppelin's `Ownable` or a Gnosis Safe). If the intention is for a fixed-supply, non-pausable token, ensure this design choice is clearly documented.


### `I-01` — Standard ERC-20 `approve` Race Condition  *(Severity: Informational · Status: Unresolved)*

The `approve` function in the ERC-20 standard is susceptible to a known front-running vulnerability. If a user increases an existing allowance for a spender, a malicious actor could front-run this transaction, spend the original allowance, and then the user's new allowance would also be spent, leading to a double-spend of the intended allowance amount. This is a limitation of the ERC-20 standard itself, not a flaw in this specific implementation.

**Recommendation:** Users should be advised to first set their allowance to zero before increasing it to a new value. Alternatively, consider using `increaseAllowance` and `decreaseAllowance` functions (if implemented) which mitigate this specific race condition, though they are not part of the core ERC-20 standard.


### `I-02` — Unused `SafeIntrospection` Library  *(Severity: Informational · Status: Unresolved)*

The `SafeIntrospection` library is included in the provided source code, but its functions are not called or utilized by the `PreIPOToken` contract. Including unused libraries can increase contract bytecode size and potentially introduce unnecessary complexity, even if the library itself is secure.

**Recommendation:** Remove the `SafeIntrospection` library if it is not intended to be used by `PreIPOToken` or any directly derived contracts. If it is part of a larger codebase and intended for future use by other components, ensure its inclusion is justified.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x1d80...7fe6`](https://bscscan.com/address/0x1d80392d12caaaf9e333bb0bb7f021eacf297fe6) |
| **Network** | BNB Chain |
| **Price** | $18.9300 |
| **24h Volume** | $5.14M |
| **Liquidity** | $1.08M |
| **Volume / Liquidity** | 4.7× |
| **Token Age** | 1d |
| **Top-10 Holders** | 52.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 12088 buys / 11284 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xc626fce3cf3781c56fe7d31f87250a8da3540a34)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/paimon-polymarket-spv-token-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-25*
