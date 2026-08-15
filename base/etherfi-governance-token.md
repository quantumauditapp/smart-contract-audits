---
token: ether.fi governance token
ticker: ETHFI
network: base
risk_score: 65
status: high
date: 2026-08-15
---

# ether.fi governance token (ETHFI) — Smart Contract Security Analysis | Base

> **Risk Score: 65/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/etherfi-governance-token-base)

---

## Audit Summary

The EthfiL2Token contract is an upgradeable ERC20 token built upon battle-tested OpenZeppelin libraries, incorporating UUPS for upgrades, Ownable2Step for ownership, and AccessControl for roles. It includes custom minting/burning functionality controlled by a designated minter role and pausable features. While the architecture is robust and leverages well-audited components, the centralized control over token supply and the pausable functionality introduce medium-level risks. Several informational findings highlight areas for potential optimization or clarity.

> **Final Recommendation:** Prioritize mitigating the risks associated with centralized control over token supply by exploring mechanisms such as timelocks for critical `setMinter` operations or multi-signature requirements for large mint/burn actions. Clearly document the intentional disabling of the `burnFrom` function to manage expectations for integrators and users. Review the necessity of separate pauser/unpauser roles and consider consolidating for simplicity if not strictly required for operational security. Ensure robust operational procedures are in place for all privileged roles, especially the `minter` and `PAUSER_ROLE`.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract leverages battle-tested OpenZeppelin libraries for ERC20, access control, and upgradeability (UUPS), enhancing its technical security (7.1 Architecture, 7.2 Code Security). Custom… |
| **Governance / Economics** | 3/10 | High | The contract's economic model is straightforward, primarily an ERC20 token with minting and burning capabilities (7.4 Economic). Control over token supply is centralized with a `minter` role, which… |
| **Upgrades** | 1/10 | High | The contract utilizes the UUPS proxy pattern, allowing for secure and controlled upgrades, with `_authorizeUpgrade` restricted to the owner (7.7 Upgrades). Initialization is handled through… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Uups |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 55.8% |
| **Top-3 Unlocked** | ⚠️ 99.5% |

## Security Findings

_🟠 1 High · 🟡 2 Medium · ⚪ 3 Informational_

### `H-01` — Centralized Control over Token Supply  *(Severity: High · Status: Unresolved)*

The `minter` role has the ability to mint and burn an arbitrary amount of tokens, directly impacting the total supply and token value. While the `minter` is set by the `owner` (a multisig), this represents a significant centralization of power over the token's economy (7.4 Economic).

**Recommendation:** Implement a timelock for `setMinter` or introduce a multi-signature confirmation for minting/burning large amounts. Alternatively, transition towards a decentralized governance model for supply control to reduce single points of failure and enhance trust.


### `M-01` — Pausable Functionality Impact  *(Severity: Medium · Status: Unresolved)*

The contract includes `PausableUpgradeable` functionality, allowing an address with `PAUSER_ROLE` to halt all token transfers. This can disrupt user operations and liquidity. While controlled by a role, it's a powerful emergency stop that could be misused or triggered accidentally, affecting the token's utility and market stability (7.4 Economic, 7.8 Operations).

**Recommendation:** Ensure robust operational procedures and multi-signature control for the `PAUSER_ROLE`. Consider implementing a timelock for `pause()` or `unpause()` actions, or a community-driven unpause mechanism to provide checks and balances.


### `M-02` — Disabled `burnFrom` Functionality  *(Severity: Medium · Status: Unresolved)*

The `burnFrom` function, typically available in ERC20Burnable tokens, is explicitly overridden to `revert UnimplementedMethod()`. This deviates from standard ERC20Burnable behavior and might cause issues for integrations or users expecting this functionality, potentially leading to unexpected failures in dApps or services that rely on it (7.2 Code Security).

**Recommendation:** Clearly document this deviation in external-facing materials and API specifications. Evaluate if this restriction is truly necessary and if it might hinder future integrations or user experience. If `burnFrom` is not intended, consider removing `ERC20BurnableUpgradeable` inheritance if possible, or provide a more specific error message.


### `I-01` — Unused `ERC20VotesUpgradeable` Functionality  *(Severity: Informational · Status: Unresolved)*

The contract inherits `ERC20VotesUpgradeable` but does not implement any voting-related logic or integrate with a governance system within the provided code. This adds complexity and bytecode size without immediate functional benefit (7.1 Architecture).

**Recommendation:** If voting functionality is not planned for the immediate future, consider removing the inheritance to reduce contract complexity and gas costs. If it is planned, ensure a clear roadmap for its integration and document its future purpose.


### `I-02` — Separate PAUSER_ROLE and UNPAUSER_ROLE  *(Severity: Informational · Status: Unresolved)*

The contract defines distinct `PAUSER_ROLE` and `UNPAUSER_ROLE`. While this allows for separation of duties, it also introduces additional complexity in role management. A single `PAUSER_ROLE` is typically sufficient to toggle the paused state (7.3 Access Control).

**Recommendation:** Review the necessity of having separate roles for pausing and unpausing. If the intent is to prevent a single entity from both pausing and unpausing, ensure the roles are assigned to different, independent entities. Otherwise, consider consolidating to a single `PAUSER_ROLE` for simplicity in role management.


### `I-03` — Owner as Default Admin Role  *(Severity: Informational · Status: Unresolved)*

In `initializeV2`, the contract owner is automatically granted the `DEFAULT_ADMIN_ROLE`. This means the owner has full administrative control over all other roles (e.g., `PAUSER_ROLE`, `UNPAUSER_ROLE`). While common, it centralizes significant power within the owner's control (7.3 Access Control, 7.5 Governance).

**Recommendation:** Document this centralization of power. For enhanced decentralization, consider transferring the `DEFAULT_ADMIN_ROLE` to a separate governance contract or a more distributed multi-signature setup, distinct from the primary contract owner, to distribute administrative control.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x6c24...2aa2`](https://basescan.org/address/0x6c240dda6b5c336df09a4d011139beaaa1ea2aa2) |
| **Network** | Base |
| **Price** | $0.4822 |
| **24h Volume** | $39.6K |
| **Liquidity** | $130.6K |
| **Volume / Liquidity** | 0.3× |
| **Token Age** | 1y |
| **Top-10 Holders** | 81.5% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 161 buys / 142 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0x3de2a8642859649d22d4a6f6a87b1441c51fdf8bf2bcd8864628a6a0f7119843)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/etherfi-governance-token-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-15*
