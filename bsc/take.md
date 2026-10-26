---
token: TAKE
ticker: TAKE
network: bsc
risk_score: 45
status: medium
date: 2026-09-25
---

# TAKE (TAKE) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 45/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/take-bsc)

---

## Audit Summary

The audit of the TokenImpl contract, deployed as an upgradeable UUPS proxy on BSC, identified a High-severity issue related to irreversible transfer mode changes, alongside Medium-severity concerns regarding custom storage slot usage and highly centralized control. The contract implements standard ERC-20 functionalities with additional pausing and transfer restriction mechanisms.

> **Final Recommendation:** Address the High-severity issue by modifying the `setTransferMode` function to allow changes from `NORMAL` mode, ensuring the intended flexibility of transfer restrictions. Carefully review the custom storage slot usage to confirm it is robust against future OpenZeppelin upgrades or other storage modifications. Consider implementing a multi-signature wallet for critical roles like `DEFAULT_ADMIN_ROLE`, `ADMIN_ROLE`, and `MINTER_ROLE` to mitigate centralization risks and enhance security.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract leverages well-audited OpenZeppelin upgradeable components for its ERC-20, pausing, access control, and reentrancy guard features (7.2 Code Security). The UUPS upgrade mechanism is… |
| **Governance / Economics** | 5/10 | Medium | The contract exhibits a highly centralized governance and economic model, with `MINTER_ROLE`, `ADMIN_ROLE`, and `transferController` possessing significant power over token supply and transferability… |
| **Upgrades** | 6/10 | Medium | The contract correctly implements the UUPS upgradeable proxy pattern, with `_authorizeUpgrade` restricted to the `DEFAULT_ADMIN_ROLE` (7.7 Upgrades). This provides a secure mechanism for future… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 3 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `M-01` — Custom Storage Slot Usage  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract utilizes a custom storage slot (`TOKEN_STATE_LOCATION`) for the `TokenState` struct via inline assembly. While a large, seemingly random hash is used, this non-standard approach for defining storage locations in an upgradeable contract introduces a risk of storage collisions. Such collisions could occur with OpenZeppelin's internal storage layout in future upgrades or with other custom storage variables, leading to data corruption or unexpected behavior.

**Recommendation:** While the current hash likely avoids immediate collision, it is generally safer to rely on OpenZeppelin's `_GAP` mechanism for custom storage in upgradeable contracts or to use a more robust method for calculating unique storage slots. If custom assembly is deemed necessary, ensure a thorough analysis of potential collision vectors, including future OpenZeppelin contract versions.


### `M-02` — High Centralization of Control  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract design grants significant centralized control to specific roles. The `MINTER_ROLE` has unlimited minting and burning capabilities, directly impacting token supply. The `ADMIN_ROLE` can `pause`/`unpause` transfers and set the `transferController`. The `transferController` can then dictate the `transferMode`, which can halt all transfers (`RESTRICTED`) or limit them to the controller (`CONTROLLED`). This concentration of power creates a single point of failure and a high trust requirement in the holders of these roles.

**Recommendation:** Implement multi-signature wallet control for the `DEFAULT_ADMIN_ROLE`, `ADMIN_ROLE`, and `MINTER_ROLE` to distribute control and reduce the risk associated with a single compromised or malicious entity. Consider introducing time-locks for critical administrative actions to provide a window for community review or emergency intervention.


### `M-03` — Irreversible Transfer Mode Change  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `setTransferMode` function contains a conditional check `if ($.transferMode != TransferMode.NORMAL)` which prevents any changes to the transfer mode if the current mode is `NORMAL`. This means that once the token's transfer mode is set to `NORMAL`, it cannot be subsequently changed back to `RESTRICTED` or `CONTROLLED`, permanently disabling the ability to impose transfer restrictions. This significantly limits the operational flexibility and emergency response capabilities of the contract administrators.

**Recommendation:** Remove or modify the `if ($.transferMode != TransferMode.NORMAL)` condition in the `setTransferMode` function to allow the `transferController` to change the transfer mode regardless of its current state, provided the `newValue` is valid.


### `L-01` — Limited Scope of `burn` Function for MINTER_ROLE  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `burn` function, accessible only by the `MINTER_ROLE`, is implemented as `_burn(msg.sender, amount)`. This means a minter can only burn tokens from their *own* balance. If the intention was for the `MINTER_ROLE` to manage the overall token supply by burning tokens from any address (e.g., a treasury or a specific user's balance), the function signature would typically include an `address from` parameter. As implemented, its utility for general supply management by the minter is limited to their personal holdings.

**Recommendation:** Clarify the intended functionality of the `burn` function. If the `MINTER_ROLE` should be able to burn tokens from arbitrary addresses, modify the function to accept an `address from` parameter and ensure appropriate access control checks are in place (e.g., `_approve` or `_permit` mechanisms if burning from others' balances). If the current behavior is intended, document this limitation clearly.


### `I-01` — Initial Transfer Mode Default to `CONTROLLED`  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). Upon initialization, the `transferMode` is set to `TransferMode.MAX_VALUE`, which corresponds to `CONTROLLED` mode. In `CONTROLLED` mode, token transfers are restricted such that either the sender or the receiver must be the designated `transferController`. This means that immediately after deployment and initialization, the token's transfer functionality is significantly limited, potentially impacting initial liquidity provision or user interactions.

**Recommendation:** Ensure that all stakeholders are aware of the initial `CONTROLLED` transfer mode and its implications. Clearly communicate the process and conditions under which the `transferMode` can be changed to `NORMAL` (if desired) and the irreversible nature of that change (as per H-01).

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xe747...e197`](https://bscscan.com/address/0xe747e54783ba3f77a8e5251a3cba19ebe9c0e197) |
| **Network** | BNB Chain |
| **Price** | $0.05871 |
| **24h Volume** | $3.56M |
| **Liquidity** | $435.4K |
| **Volume / Liquidity** | 8.2× |
| **Token Age** | 1y |
| **Top-10 Holders** | 94.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 23477 buys / 24185 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x46bb9a29bfa5397b30a96a316875496ec2556dd2)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/take-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-25*
