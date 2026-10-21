---
token: Goldfish
ticker: GGBR
network: ethereum
risk_score: 100
status: critical
date: 2026-09-01
---

# Goldfish (GGBR) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 100/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/goldfish-eth)

---

## Audit Summary

The GoldfishToken contract, an upgradeable ERC-20, exhibits a high degree of centralization, particularly concerning the `DEFAULT_ADMIN_ROLE`. A critical finding highlights the `forceTransfer` function, which acts as a backdoor allowing the admin to move any user's tokens. The absence of multi-signature protection or time-locks for critical operations further exacerbates these risks. While the contract leverages well-audited OpenZeppelin libraries for core functionalities and implements granular access control for specific actions, the overarching administrative power presents significant security and economic concerns.

> **Final Recommendation:** It is strongly recommended to implement a robust multi-signature wallet (e.g., Gnosis Safe) for the `DEFAULT_ADMIN_ROLE` and other critical roles to mitigate the single point of failure risk. The `forceTransfer` function should be removed or protected by a multi-signature wallet with a time-lock and potentially a governance vote. Additionally, consider implementing stricter controls or governance for `maxSupply` adjustments to prevent arbitrary inflation.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 4/10 | Medium | The contract is built upon battle-tested OpenZeppelin libraries (ERC20Burnable, Pausable, AccessControl, UUPS), providing a solid foundation for its core ERC-20 functionalities (7.2 Code Security).… |
| **Governance / Economics** | 1/10 | High | The contract implements granular roles (PAUSER_ROLE, FREEZER_ROLE, SUPPLY_MANAGER_ROLE) which is a positive for delegated responsibilities (7.5 Governance). However, the `DEFAULT_ADMIN_ROLE` holds… |
| **Upgrades** | 1/10 | High | The contract correctly implements the UUPS upgrade pattern using OpenZeppelin's `UUPSUpgradeable` module (7.7 Upgrades). The `_authorizeUpgrade` function is appropriately restricted to the… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Uups |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 96.0% |
| **Top-3 Unlocked** | ⚠️ 98.8% |

## Security Findings

_🔴 1 Critical · 🟠 1 High · 🟡 1 Medium · 🟢 2 Low_

### `C-01` — Extreme Centralization and Backdoor Functionality (`forceTransfer`)  *(Severity: Critical · Status: Unresolved)*

The `DEFAULT_ADMIN_ROLE` possesses extensive control, including the ability to upgrade the contract, blacklist accounts, set the minter, and crucially, execute `forceTransfer`. The `forceTransfer` function allows the admin to transfer any amount of tokens from any address to any other address without the token holder's consent. This represents a severe centralization risk and a direct backdoor, enabling arbitrary seizure or redistribution of user funds.

**Recommendation:** Remove or significantly restrict the `forceTransfer` function. If such a function is deemed absolutely necessary for emergency scenarios, it should be protected by a multi-signature wallet with a time-lock, require a governance vote, or be limited to specific, predefined emergency conditions.


### `H-01` — Lack of Multi-signature / Time-lock for Critical Operations  *(Severity: High · Status: Unresolved)*

All critical administrative roles (`DEFAULT_ADMIN_ROLE`, `PAUSER_ROLE`, `FREEZER_ROLE`, `SUPPLY_MANAGER_ROLE`) are initially granted to the deployer (`msg.sender`) and can be managed by the `DEFAULT_ADMIN_ROLE`. There are no multi-signature wallet requirements or time-locks implemented for sensitive operations such as contract upgrades, setting the minter, blacklisting, freezing, or using `forceTransfer`. This creates a single point of failure, making the protocol highly vulnerable to compromise of a single private key or malicious insider actions.

**Recommendation:** Implement a robust access control mechanism for critical roles, preferably using a multi-signature wallet (e.g., Gnosis Safe) for `DEFAULT_ADMIN_ROLE` and other sensitive roles. Consider adding time-locks for highly impactful operations like contract upgrades or `forceTransfer` to provide a window for users to react to potentially malicious actions.


### `M-01` — Arbitrary `maxSupply` Increase  *(Severity: Medium · Status: Unresolved)*

The `setMaxSupply` function, callable by the `SUPPLY_MANAGER_ROLE`, allows increasing the `maxSupply` to an arbitrarily high value. While it prevents reducing the supply below the current `totalSupply()`, there is no upper bound or governance mechanism to limit how much the `maxSupply` can be increased. This could lead to unexpected and significant token inflation if the `SUPPLY_MANAGER_ROLE` is compromised or acts maliciously, devaluing existing token holdings.

**Recommendation:** Implement a more constrained mechanism for `maxSupply` adjustments. Consider adding a maximum allowable increase percentage per operation, a time-lock for changes, or requiring a governance vote for significant increases. Alternatively, define a hard-coded, immutable maximum supply if the token is intended to be deflationary or have a fixed cap.


### `L-01` — Disabled `burnFrom` Functionality  *(Severity: Low · Status: Unresolved)*

The `burnFrom` function, a standard part of the ERC20Burnable extension, has been explicitly disabled by reverting all calls. This design choice removes a common functionality that allows approved third parties (e.g., DeFi protocols) to burn tokens on behalf of a user. While a design decision, it limits the composability and utility of the token within the broader DeFi ecosystem.

**Recommendation:** Review the necessity of disabling `burnFrom`. If the intention is to prevent specific types of interactions, consider if alternative mechanisms or more granular controls could achieve the same security goals without completely removing standard functionality. If the decision is final, ensure clear documentation for users and integrators.


### `L-02` — `batchTransfer` Self-Transfer Restriction  *(Severity: Low · Status: Unresolved)*

The `batchTransfer` function explicitly disallows self-transfers within the batch by including the check `require(_recipients[i] != msg.sender, "Self-transfer not allowed");`. While not a security vulnerability, this is an unusual restriction for a batch transfer function. Users might expect to be able to include their own address in a batch for various reasons (e.g., consolidating funds, rebalancing).

**Recommendation:** Re-evaluate the necessity of preventing self-transfers in `batchTransfer`. If there's no specific security rationale, removing this restriction would improve user experience and align with common token transfer patterns. If it's a deliberate design choice, ensure it's clearly documented.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x7e2a...b71a`](https://etherscan.io/address/0x7e2ac793f3e692f388e66c7dc28f739d13b0b71a) |
| **Network** | Ethereum |
| **Price** | $4.1700 |
| **24h Volume** | $1.5K |
| **Liquidity** | $181.2K |
| **Volume / Liquidity** | 0.0× |
| **Token Age** | 10mo |
| **Top-10 Holders** | 97.5% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 123 buys / 195 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x75a5a265d21bc89ec130f18edde2b49a4b200dac)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/goldfish-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-01*
