---
token: trUSD
ticker: TRUSD
network: ethereum
risk_score: 75
status: critical
date: 2026-08-12
---

# trUSD (TRUSD) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 75/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/trusd-eth)

---

## Audit Summary

The TrUSD contract implements an upgradeable ERC-20 token with a two-tiered access control system. While leveraging battle-tested OpenZeppelin libraries and a multisig for the primary admin role, a significant risk arises from the immediate execution capabilities of the TIMELOCK_ADMIN_ROLE for critical functions like token minting and contract upgrades, lacking the timelock present for the DEFAULT_ADMIN_ROLE. This centralization of immediate power, if compromised, could lead to severe economic or operational consequences.

> **Final Recommendation:** To enhance the security posture of the TrUSD contract, it is strongly recommended to implement a timelock mechanism for all critical actions performed by the TIMELOCK_ADMIN_ROLE, particularly for `setMinter` and `_authorizeUpgrade`. This would introduce a necessary delay, allowing for scrutiny and intervention in case of a compromise or error. Additionally, ensure the TIMELOCK_ADMIN_ROLE is controlled by a robust, high-threshold multi-signature wallet, and consider adding a timelock or additional approval steps for the `setTimelockAdmin` function to prevent immediate role transfers.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract demonstrates good technical architecture (7.1) by utilizing OpenZeppelin's upgradeable ERC-20 and AccessControlDefaultAdminRules libraries, ensuring a solid foundation for code security… |
| **Governance / Economics** | 3/10 | High | The governance and economic model (7.5, 7.4) benefits from a two-tiered access control structure, where the DEFAULT_ADMIN_ROLE (assumed multisig with a 1-day timelock) controls the… |
| **Upgrades** | 1/10 | High | The contract correctly implements the UUPS upgradeability pattern (7.7) using OpenZeppelin's `UUPSUpgradeable` module, overriding `_authorizeUpgrade` to restrict upgrade authorization to the… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Uups |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 1 Medium · 🟢 1 Low_

### `H-01` — Immediate and Centralized Control over Critical Functions (Minting & Upgrades)  *(Severity: High · Status: Unresolved)*

The `TIMELOCK_ADMIN_ROLE` has immediate and centralized control over critical functions: `setMinter` (allowing unlimited token minting) and `_authorizeUpgrade` (allowing instant contract upgrades). Unlike the `DEFAULT_ADMIN_ROLE`, which has a 1-day timelock, actions by the `TIMELOCK_ADMIN_ROLE` can be executed instantly. This concentration of power, coupled with the lack of a timelock for these actions, presents a significant risk of immediate economic manipulation or malicious contract changes if the `TIMELOCK_ADMIN_ROLE` is compromised or misused. (7.3 Access Control, 7.4 Economic, 7.7 Upgrades)

**Recommendation:** Implement a timelock mechanism for all critical actions performed by the `TIMELOCK_ADMIN_ROLE`, specifically for `setMinter` and `_authorizeUpgrade`. This would introduce a delay, allowing for community review and intervention. Additionally, ensure the `TIMELOCK_ADMIN_ROLE` itself is controlled by a robust, multi-signature wallet with a high threshold to mitigate the centralization risk.


### `M-01` — TIMELOCK_ADMIN_ROLE Transfer Mechanism Vulnerability  *(Severity: Medium · Status: Unresolved)*

The `setTimelockAdmin` function allows the current `TIMELOCK_ADMIN_ROLE` to transfer its role to a new address. If the `TIMELOCK_ADMIN_ROLE` is controlled by a single EOA or a low-threshold multisig, a compromise of this entity could lead to an unauthorized transfer of the role, potentially bypassing the `DEFAULT_ADMIN_ROLE`'s timelock for subsequent actions. (7.3 Access Control, 7.8 Operations)

**Recommendation:** Ensure the `TIMELOCK_ADMIN_ROLE` is managed by a highly secure, multi-signature wallet. Consider adding a timelock to the `setTimelockAdmin` function itself, or requiring approval from the `DEFAULT_ADMIN_ROLE` for such a critical transfer.


### `L-01` — One-Time `initializeTimelockAdmin` Call Risk  *(Severity: Low · Status: Unresolved)*

The `initializeTimelockAdmin` function can only be called once by the `DEFAULT_ADMIN_ROLE` to set the initial `TIMELOCK_ADMIN_ROLE`. If an incorrect or compromised address is set during this initial call, it would require the `DEFAULT_ADMIN_ROLE` to manually revoke and regrant the role, which is possible but adds operational complexity and potential for error. (7.8 Operations)

**Recommendation:** Exercise extreme caution and verify the `timelockAdmin` address thoroughly before calling `initializeTimelockAdmin`. Implement robust pre-deployment checks and consider a multi-step initialization process or a mechanism for the `DEFAULT_ADMIN_ROLE` to correct the initial assignment more smoothly if needed.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xd058...1697`](https://etherscan.io/address/0xd0580192e98ea6ceb9c7b6191ed2e27560911697) |
| **Network** | Ethereum |
| **Price** | $1.0002 |
| **24h Volume** | $1.39M |
| **Liquidity** | $6.17M |
| **Volume / Liquidity** | 0.2× |
| **Token Age** | 26d |
| **Top-10 Holders** | 99.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 121 buys / 46 sells |

## Security Flags (1/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0xb723a224c9acf3891b20437b4d55dd45600f5fa3)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/trusd-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-12*
