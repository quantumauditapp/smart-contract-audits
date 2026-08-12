---
token: Towns
ticker: TOWNS
network: base
risk_score: 71
status: critical
date: 2026-08-12
---

# Towns (TOWNS) — Smart Contract Security Analysis | Base

> **Risk Score: 71/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/towns-base)

---

## Audit Summary

The Towns contract serves as an ERC-20 token with voting capabilities, cross-chain mint/burn functionality, and a unique token transfer lock mechanism tied to delegation. It is deployed as a UUPS upgradeable proxy on the Base network. The contract leverages well-audited Solady libraries and OpenZeppelin components, demonstrating a robust architectural foundation. The primary area of concern identified is the fixed and significant 30-day token transfer lock imposed on users who undelegate their voting power, which could lead to unexpected liquidity restrictions.

> **Final Recommendation:** It is recommended to ensure comprehensive user education regarding the fixed 30-day token transfer lock that activates upon undelegation. Clear communication channels, documentation, and user interface warnings should highlight this significant cooldown period to prevent unexpected liquidity issues for token holders. Additionally, consider documenting the design choice behind the `_canLock()` function always returning `false` to clarify the intended behavior of the `LockBase` contract's `onlyAllowed` modifier for future development and auditing efforts.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract exhibits a strong technical foundation (7.1 Architecture), utilizing battle-tested Solady libraries for ERC20Votes, Ownable, and UUPSUpgradeable, along with OpenZeppelin interfaces.… |
| **Governance / Economics** | 3/10 | High | The Towns token incorporates standard ERC20Votes functionality, allowing for robust on-chain governance (7.5 Governance) through delegation. The economic model (7.4 Economic) includes a mechanism to… |
| **Upgrades** | 1/10 | High | The contract implements the UUPS upgradeability pattern (7.7 Upgrades), which is a secure and widely adopted standard. The `_authorizeUpgrade` function is correctly overridden to restrict upgrade… |

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

_🟡 1 Medium · ⚪ 1 Informational_

### `M-01` — Fixed and Significant Token Transfer Lock on Undelegation  *(Severity: Medium · Status: Unresolved)*

The `Towns` contract implements a token transfer lock mechanism tied to voting delegation. When a user undelegates their voting power (by delegating to `address(0)`), their tokens become subject to a 30-day transfer lock. This `defaultCooldown` is set during initialization via `__LockBase_init(30 days)` and cannot be modified later, making the 30-day lock period a permanent and unchangeable feature. While this is an intended design, its fixed and substantial duration could lead to unexpected liquidity restrictions for users who are unaware of this cooldown period, potentially impacting user experience and token utility.

**Recommendation:** Ensure that the fixed 30-day token transfer lock upon undelegation is clearly communicated to all users through official documentation, user interfaces, and any relevant educational materials. Consider adding a warning or confirmation step in front-end applications when a user attempts to undelegate, explicitly stating the impending transfer lock duration. While the contract design makes this immutable, transparent communication is crucial to manage user expectations.


### `I-01` — Unused `onlyAllowed` Modifier in `LockBase`  *(Severity: Informational · Status: Unresolved)*

The `_canLock()` function in the `Towns` contract, which is an override from `LockBase`, always returns `false`. This design choice renders the `onlyAllowed` modifier within the `LockBase` contract effectively unusable. While `Towns` does not directly expose any external functions that utilize this modifier, its presence in the inherited `LockBase` contract, coupled with `_canLock()` always returning `false`, indicates a potential design inconsistency or an unimplemented feature from the `ILock` interface (e.g., `enableLock`, `disableLock`, `setLockCooldown` are not implemented in `Towns` with this modifier).

**Recommendation:** Document the explicit design decision behind `_canLock()` always returning `false` and the implications for the `onlyAllowed` modifier in `LockBase`. If the `onlyAllowed` modifier and associated external functions from `ILock` were never intended to be used or exposed, consider removing them from `LockBase` or clarifying their purpose to avoid confusion for future developers or auditors. If they were intended, ensure proper implementation and exposure.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x0000...9a38`](https://basescan.org/address/0x00000000a22c618fd6b4d7e9a335c4b96b189a38) |
| **Network** | Base |
| **Price** | $0.002338 |
| **24h Volume** | $137.9K |
| **Liquidity** | $199.8K |
| **Volume / Liquidity** | 0.7× |
| **Token Age** | 1y |
| **Top-10 Holders** | 76.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 489 buys / 638 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0x48be08d21fccf3f793783c23c33555f5e0c2b7cd)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/towns-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-12*
