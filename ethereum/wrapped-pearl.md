---
token: Wrapped Pearl
ticker: WPRL
network: ethereum
risk_score: 58
status: medium
date: 2026-09-18
---

# Wrapped Pearl (WPRL) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 58/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/wrapped-pearl-eth)

---

## Audit Summary

The WPearl contract implements an upgradeable ERC-20 token with custom freezing capabilities and a fixed maximum supply. It leverages OpenZeppelin's upgradeable contracts and access control mechanisms. While the core logic is sound and standard patterns are used, significant power is concentrated in administrative roles, and a token rescue function is absent. The upgrade mechanism includes a timelock and upward-only delay, enhancing security.

> **Final Recommendation:** Prioritize the security of the `DEFAULT_ADMIN_ROLE` and `bridgeController` by implementing robust multi-signature controls with high thresholds and strict operational security procedures. Consider integrating a token rescue mechanism to prevent permanent loss of accidentally sent assets. Ensure all stakeholders understand the implications of the `revokeFreezeAbility` function due to its irreversible nature.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 7/10 | Low | The contract utilizes a robust architecture based on OpenZeppelin's upgradeable ERC-20, AccessControl, and UUPS proxy patterns, which are well-audited and widely adopted. Custom logic for freezing… |
| **Governance / Economics** | 4/10 | Medium | The economic model includes a `MAX_SUPPLY` of 2.1 billion WPRL, preventing uncontrolled inflation. Minting and burning are centralized under a `bridgeController` role, which is a significant point of… |
| **Upgrades** | 1/10 | High | The contract implements the UUPS upgradeability pattern, a standard and secure method for upgradeable contracts (7.7 Upgrades). Upgrades are controlled by the `DEFAULT_ADMIN_ROLE` and incorporate a… |

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

_🟡 2 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `M-01` — Missing Emergency Token Rescue Function  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract lacks a function to rescue accidentally sent ERC-20 tokens (other than WPRL itself) or native currency. If any other token or ETH is mistakenly transferred to the contract address, it will be permanently locked and inaccessible, leading to irretrievable loss of funds. (7.8 Operations)

**Recommendation:** Implement a `rescueTokens(address tokenAddress, address to, uint256 amount)` function, restricted to the `DEFAULT_ADMIN_ROLE`, to allow recovery of mistakenly sent tokens. This function should explicitly prevent the rescue of the contract's own token (`address(this)`) to avoid accidental draining of the token supply.


### `M-02` — Centralized Control of Critical Functions  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `DEFAULT_ADMIN_ROLE` possesses extensive power, including the ability to grant/revoke all other roles (e.g., `bridgeController`, `FREEZER_ROLE`, `REVOKE_FREEZE_ROLE`), propose/cancel upgrades, and adjust the upgrade delay. The `bridgeController` role has sole authority to `mint` new tokens (up to `MAX_SUPPLY`) and `burnFrom` any account. The `FREEZER_ROLE` can freeze and unfreeze accounts, impacting token transferability. While `AccessControlDefaultAdminRulesUpgradeable` provides an initial delay for admin actions, the concentration of power in these roles represents a significant centralization risk. A compromise

**Recommendation:** Ensure that the `DEFAULT_ADMIN_ROLE` and `bridgeController` are controlled by robust multi-signature wallets with high thresholds, or a well-governed DAO. Implement strict operational security procedures, including multi-party approval and time-locks for critical actions, to mitigate the risk of a single point of failure or key compromise.


### `L-01` — Permanent Revocation of Freeze Ability  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `revokeFreezeAbility()` function, callable by `REVOKE_FREEZE_ROLE`, permanently sets `freezeAbilityRevoked = true` if `frozenCount == 0`. Once this flag is set, the `FREEZER_ROLE` can no longer be granted, and accounts cannot be frozen or unfrozen. This is an irreversible state change designed to permanently disable the freeze mechanism. While intentional, it represents a critical, one-time decision with lasting implications for the token's censorship resistance. (7.3 Access Control, 7.4 Economic)

**Recommendation:** Ensure that the implications of `revokeFreezeAbility` are fully understood by the `REVOKE_FREEZE_ROLE` holders. If not already covered by the admin's multi-sig or DAO, consider adding a multi-step process or a governance vote for such a critical, irreversible action to ensure broad consensus.


### `I-01` — `burn()` Function Reverts by Design  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `burn()` function, which is part of the `ERC20BurnableUpgradeable` standard, is explicitly overridden to `revert("WPearl: use BridgeController.requestBurn()")`. This design choice centralizes all burning operations through the `bridgeController` via the `burnFrom` function. This deviates from the standard ERC-20 `burn` behavior where any token holder can burn their own tokens. (7.1 Architecture, 7.2 Code Security)

**Recommendation:** Document this design choice clearly for users and integrators, explaining that direct burning by token holders is not supported and all burn requests must be initiated or processed through the `bridgeController`.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x0769...cb00`](https://etherscan.io/address/0x07696dcab55e62cfef953666b29fe1970518cb00) |
| **Network** | Ethereum |
| **Price** | $0.9209 |
| **24h Volume** | $335.1K |
| **Liquidity** | $236.1K |
| **Volume / Liquidity** | 1.4× |
| **Token Age** | 4mo |
| **Top-10 Holders** | 49.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 231 buys / 394 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x89a67c6dee35db9815da2fb9191f0998a8b37c39)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/wrapped-pearl-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-18*
