---
token: STBL_Token - STBL Governance Token
ticker: STBL
network: bsc
risk_score: 76
status: critical
date: 2026-08-17
---

# STBL_Token - STBL Governance Token (STBL) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 76/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/stbltoken-stbl-governance-token-bsc)

---

## Audit Summary

The STBL_Token contract is an upgradeable ERC-20 token utilizing OpenZeppelin's battle-tested libraries for access control, pausing, and UUPS upgradeability. The technical implementation is robust, showing no critical code-level vulnerabilities like reentrancy or integer overflows. However, the contract exhibits a high degree of centralization, with the DEFAULT_ADMIN_ROLE holding significant power over critical functions such as role management, contract upgrades, and token supply manipulation (via MINTER_ROLE and BRIDGE_ROLE). This centralization, while common for initial deployments, introduces a single point of failure and elevates the overall risk to Medium.

> **Final Recommendation:** To mitigate the risks associated with centralized control, it is strongly recommended to secure the `DEFAULT_ADMIN_ROLE` with a robust multi-signature wallet (e.g., Gnosis Safe) requiring multiple independent approvals for critical operations. Consider implementing a time-lock mechanism for sensitive administrative actions, such as role changes or upgrades, to provide a window for community review or emergency intervention. Regularly review and audit the addresses holding administrative roles to ensure their security and integrity.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The STBL_Token contract leverages battle-tested OpenZeppelin libraries for its core ERC-20 functionality, access control (7.3), pausing, and UUPS upgradeability (7.7). The code demonstrates good… |
| **Governance / Economics** | 1/10 | High | The contract implements a `MAX_CAP` to limit total token supply, and distinct roles (`MINTER_ROLE`, `BRIDGE_ROLE`, `PAUSE_ROLE`) are used for specific actions, providing granular control (7.4). The… |
| **Upgrades** | 1/10 | High | The contract correctly implements the UUPS upgradeability pattern using OpenZeppelin's `UUPSUpgradeable` module (7.7). The `_authorizeUpgrade` function is properly overridden and protected by the… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Uups |
| **Implementation** | ✅ Verified source |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 1 Medium · 🟢 1 Low_

### `H-01` — Centralized Control Over Critical Functions  *(Severity: High · Status: Unresolved)*

The `DEFAULT_ADMIN_ROLE` in the `STBL_Token` contract possesses extensive control over critical functions. This role can grant/revoke all other roles (`MINTER_ROLE`, `BRIDGE_ROLE`, `PAUSE_ROLE`, `UPGRADER_ROLE`), initiate contract upgrades, and update the trusted forwarder. The `MINTER_ROLE` and `BRIDGE_ROLE` can mint and burn tokens up to the `MAX_CAP`. This high degree of centralization introduces a single point of failure; if the address holding the `DEFAULT_ADMIN_ROLE` is compromised, an attacker could gain full control over the token's supply, upgrade its logic to malicious code, or pause all operations.

**Recommendation:** Implement a robust multi-signature wallet (e.g., Gnosis Safe) to control the `DEFAULT_ADMIN_ROLE` and other critical roles. For highly sensitive operations like upgrades or role management, consider adding a time-lock mechanism to allow for community review or emergency response before execution. Clearly document the operational procedures and security measures for managing these privileged roles.


### `M-01` — Redundant Role Grant in Initialization  *(Severity: Medium · Status: Unresolved)*

The `initialize()` function calls `_grantRole(DEFAULT_ADMIN_ROLE, _msgSender());` twice. While this redundancy does not introduce a functional vulnerability or error, it indicates a minor oversight in the code and could potentially lead to confusion or slight gas inefficiency if the `_grantRole` function had side effects beyond state modification.

**Recommendation:** Remove the duplicate call to `_grantRole(DEFAULT_ADMIN_ROLE, _msgSender());` from the `initialize()` function. Ensure that each role grant is performed only once to maintain code clarity and efficiency.


### `L-01` — Unnecessary SafeERC20 Usage for Self-Transfer  *(Severity: Low · Status: Unresolved)*

In the `burn` and `bridgeBurn` functions, `IERC20(address(this)).safeTransferFrom(_from, address(this), _amt);` is used. While `SafeERC20` is generally good practice for interacting with external ERC-20 tokens, using `safeTransferFrom` to transfer tokens to `address(this)` (the token contract itself) is not strictly necessary for security. The contract is interacting with its own token balance, and a direct `_transfer` or `_approve` followed by `_transferFrom` would suffice without the `SafeERC20` wrapper, as the contract's own `_transfer` logic is trusted.

**Recommendation:** Consider simplifying the `burn` and `bridgeBurn` functions by directly calling `_transfer` or `_transferFrom` if the intent is to move tokens within the contract's own context, rather than using `SafeERC20` for self-transfers. This would slightly reduce gas costs and improve readability without compromising security. Alternatively, keep the current implementation as it is harmless.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x8ded...79e3`](https://bscscan.com/address/0x8dedf84656fa932157e27c060d8613824e7979e3) |
| **Network** | BNB Chain |
| **Price** | $0.02622 |
| **24h Volume** | $2.91M |
| **Liquidity** | $1.76M |
| **Volume / Liquidity** | 1.7× |
| **Token Age** | 11mo |
| **Top-10 Holders** | 79.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 7470 buys / 8285 sells |

## Security Flags (1/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x90166b5795250fe7f0831e844121cc91799787e9)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/stbltoken-stbl-governance-token-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-17*
