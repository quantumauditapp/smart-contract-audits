---
token: WINR
ticker: WINR
network: arbitrum
risk_score: 45
status: medium
date: 2026-09-02
---

# WINR (WINR) — Smart Contract Security Analysis | Arbitrum

> **Risk Score: 45/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/winr-arb)

---

## Audit Summary

The WINR token contract implements a standard ERC20 token with custom minting and burning functionalities. It utilizes OpenZeppelin's AccessControl for role-based permissions. A significant vulnerability was identified in the `burn` function, where `MAX_SUPPLY` is reduced by the burned amount, leading to potential integer underflow and unintended tokenomics. Centralized control by the `DEFAULT_ADMIN_ROLE` also presents a medium risk.

> **Final Recommendation:** Address the critical vulnerability in the `burn` function by removing the `MAX_SUPPLY -= amount` line. `MAX_SUPPLY` should represent a fixed, absolute maximum and not be modifiable by user burns. If a dynamic maximum supply is desired, a separate, privileged function should be implemented for its adjustment. Consider implementing a pause mechanism to halt critical operations in emergencies. Ensure the `DEFAULT_ADMIN_ROLE` is managed securely, potentially through a multi-signature wallet or a time-locked governance contract.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract is built on OpenZeppelin's robust ERC20 and AccessControl libraries, providing a solid foundation for token functionality and role-based access. The `mint` function correctly implements… |
| **Governance / Economics** | 2/10 | High | The contract employs a role-based access control system, with a `MINTER_ROLE` for minting and a `DEFAULT_ADMIN_ROLE` managing all other roles (7.3 Access Control). This centralized control allows the… |
| **Upgrades** | 3/10 | High | The WINR contract is not designed with upgradeability in mind, as it does not implement any proxy patterns (7.7 Upgrades). This means that any future changes or bug fixes would require a new contract… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 99.3% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 2 Medium · ⚪ 1 Informational_

### `M-01` — Centralized Control by `DEFAULT_ADMIN_ROLE`  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract relies on OpenZeppelin's `AccessControl` for managing permissions. The `DEFAULT_ADMIN_ROLE` has the power to grant and revoke all other roles, including the `MINTER_ROLE`. This centralizes significant control over the token's minting capabilities and overall access management to a single address or a small group of addresses. A compromise of this admin key could lead to unauthorized minting or manipulation of roles.

**Recommendation:** Implement a robust security strategy for the `DEFAULT_ADMIN_ROLE`. This could involve using a multi-signature wallet (e.g., Gnosis Safe) to manage the admin key, or integrating with a decentralized governance system. Consider implementing a time-lock for critical administrative actions to provide a window for community review or emergency intervention.


### `M-02` — `MAX_SUPPLY` Underflow and Economic Manipulation in `burn` Function  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `burn` function allows any user to burn their tokens, and critically, it also decrements the `MAX_SUPPLY` variable by the burned amount (`MAX_SUPPLY -= amount`). This introduces two significant issues: 1.  **Integer Underflow:** If the current `MAX_SUPPLY` is less than the `amount` a user attempts to burn, the subtraction `MAX_SUPPLY -= amount` will cause an integer underflow, leading to a transaction revert. This effectively creates a denial of service for users attempting to burn tokens under certain conditions. 2.  **Economic Manipulation:** The `MAX_SUPPLY` variable is intended to represent the absolute maximum

**Recommendation:** Remove the line `MAX_SUPPLY -= amount` from the `burn` function. The `MAX_SUPPLY` should remain a fixed, global cap on the total supply and not be affected by individual token burns. If a mechanism to adjust the maximum supply is desired, it should be implemented as a separate, privileged function accessible only by a trusted role (e.g., `DEFAULT_ADMIN_ROLE`) and with careful consideration of its implications.


### `I-01` — Lack of Pause Mechanism  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract does not include a mechanism to pause token transfers or other critical operations in case of an emergency, such as a discovered vulnerability, a major exploit in an integrated protocol, or market instability. In such scenarios, the inability to halt operations could exacerbate losses or allow an attack to continue unchecked.

**Recommendation:** Consider integrating a pause mechanism, such as OpenZeppelin's `Pausable` contract. This would allow a designated role (e.g., a `PAUSER_ROLE` managed by the admin or a governance contract) to temporarily halt token operations. This mechanism should be used judiciously and ideally be subject to governance control or a time-lock.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xd77b...a46e`](https://arbiscan.io/address/0xd77b108d4f6cefaa0cae9506a934e825becca46e) |
| **Network** | Arbitrum |
| **Price** | $0.002863 |
| **24h Volume** | $14.5K |
| **Liquidity** | $108.2K |
| **Volume / Liquidity** | 0.1× |
| **Token Age** | 1y |
| **Top-10 Holders** | 70.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 776 buys / 576 sells |

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

- [View on DexScreener](https://dexscreener.com/arbitrum/0xc35aa1cec34e02a8acc3e5f79c22be364823094c)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/winr-arb)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-02*
