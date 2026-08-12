---
token: Holoworld AI
ticker: HOLO
network: bsc
risk_score: 47
status: high
date: 2026-08-12
---

# Holoworld AI (HOLO) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 47/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/holoworld-ai-bsc)

---

## Audit Summary

The HoloToken contract, an ERC20 token utilizing OpenZeppelin's AccessControl, was audited for security vulnerabilities. The contract implements custom roles for administration, pausing, and minting, along with a maximum supply and transfer control mechanisms. Key findings include a high-severity access control misconfiguration allowing PAUSER_ROLE self-management, and medium-severity centralization risks due to powerful privileged roles. The contract demonstrates good use of established libraries and clear logic, but the identified access control and centralization issues warrant immediate attention to enhance the protocol's security posture.

> **Final Recommendation:** It is strongly recommended to address the identified access control misconfiguration for the PAUSER_ROLE to prevent potential privilege escalation. Review the role hierarchy and ensure that critical role management is overseen by higher-level administrative roles, ideally secured by multi-signature wallets or robust governance mechanisms.
Furthermore, consider assigning critical administrative roles to multi-signature wallets or governance contracts instead of single externally owned accounts (EOAs) to mitigate centralization risks and enhance operational security. Implement comprehensive testing, especially for access control logic, to validate the intended permissions and prevent unintended behaviors.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract leverages battle-tested OpenZeppelin libraries for ERC20 and AccessControl, enhancing code security and adherence to standards (7.2 Code Security). The `_update` override correctly… |
| **Governance / Economics** | 1/10 | High | The token implements a clear `MAX_SUPPLY` and controlled minting via the `MINTER_ROLE`, providing transparency on token issuance (7.4 Economic). However, the system exhibits high centralization, with… |
| **Upgrades** | 6/10 | Medium | The contract is not designed with an upgrade mechanism (e.g., proxy pattern). Therefore, there are no upgrade-specific risks (7.7 Upgrades). Any future changes to the contract logic would require a… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 99.3% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `H-01` — PAUSER_ROLE Self-Management Allows Privilege Escalation  *(Severity: High · Status: Unresolved)*

The `_setRoleAdmin(PAUSER_ROLE, PAUSER_ROLE)` configuration in the constructor allows any account holding the `PAUSER_ROLE` to grant or revoke `PAUSER_ROLE` to/from other addresses. This bypasses the oversight of the `DEFAULT_ADMIN_ROLE` and `ADMIN_ROLE` for managing pausers. A compromised PAUSER could add more malicious PAUSERs or remove legitimate ones, effectively taking full control of the pausing mechanism without higher administrative approval (7.3 Access Control).

**Recommendation:** Change the admin role for `PAUSER_ROLE` to a higher-level administrative role, such as `DEFAULT_ADMIN_ROLE` or `ADMIN_ROLE`. For example, `_setRoleAdmin(PAUSER_ROLE, ADMIN_ROLE);` would ensure that only accounts with `ADMIN_ROLE` can manage the `PAUSER_ROLE`.


### `M-01` — High Centralization of Control  *(Severity: Medium · Status: Unresolved)*

The contract design relies heavily on privileged roles (`DEFAULT_ADMIN_ROLE`, `ADMIN_ROLE`, `PAUSER_ROLE`, `MINTER_ROLE`). These roles have significant power, including managing other roles, minting tokens up to the maximum supply, and controlling all token transfers (pausing/unpausing, whitelisting). If the private keys associated with these roles (especially if they are EOAs) are compromised, it could lead to severe consequences such as arbitrary minting, denial of service for transfers, or loss of funds (7.5 Governance, 7.8 Operations).

**Recommendation:** For critical roles, consider assigning them to multi-signature wallets or robust governance contracts instead of single externally owned accounts (EOAs). This distributes control and requires multiple approvals for sensitive operations, significantly reducing the risk of a single point of failure.


### `L-01` — Initial Role Assignments to EOAs  *(Severity: Low · Status: Unresolved)*

The constructor assigns `DEFAULT_ADMIN_ROLE` to `msg.sender` and `ADMIN_ROLE`/`PAUSER_ROLE` to `initialAdmin`/`initialPauser` addresses. If these are externally owned accounts (EOAs), they represent single points of failure. A compromise of any of these EOAs could lead to unauthorized control over critical contract functions (7.8 Operations).

**Recommendation:** While common for initial deployment, it is best practice to transfer ownership of critical roles (especially `DEFAULT_ADMIN_ROLE`) to a multi-signature wallet or a well-tested governance contract immediately after deployment. This enhances security by requiring multiple approvals for sensitive actions.


### `I-01` — Redundant `require` in `setTransfersEnabled`  *(Severity: Informational · Status: Unresolved)*

The `setTransfersEnabled` function includes `require(transfersEnabled != status, "HoloToken: status not changed");`. This check prevents setting the `transfersEnabled` state variable to its current value. While not harmful, this check is redundant as setting a state variable to its current value has no effect and consumes gas unnecessarily (7.2 Code Security).

**Recommendation:** Consider removing this `require` statement, as setting a variable to its existing value is a no-op and does not introduce a vulnerability. Alternatively, if the intent is to provide a more specific error, the message could be improved (e.g., 'Transfers are already enabled' or 'Transfers are already disabled').

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x1a5d...9497`](https://bscscan.com/address/0x1a5d7e4c3a7f940b240b7357a4bfed30d17f9497) |
| **Network** | BNB Chain |
| **Price** | $0.07438 |
| **24h Volume** | $1.96M |
| **Liquidity** | $524.2K |
| **Volume / Liquidity** | 3.7× |
| **Token Age** | 11mo |
| **Top-10 Holders** | 96.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 8383 buys / 8398 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xf7f9fc41da4b8e0d52a642af2ad38509c3e40bf0)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/holoworld-ai-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-12*
