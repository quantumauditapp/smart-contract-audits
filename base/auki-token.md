---
token: Auki Token
ticker: AUKI
network: base
risk_score: 63
status: medium
date: 2026-09-23
---

# Auki Token (AUKI) — Smart Contract Security Analysis | Base

> **Risk Score: 63/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/auki-token-base)

---

## Audit Summary

This audit reviews the `AukiToken` contract, which serves as the implementation for a UUPS proxy. While the full source code for the `AukiToken` implementation was not directly provided, the audit was conducted based on the provided interfaces, libraries, and pre-filled contract metadata, inferring a standard OpenZeppelin-based ERC20 token with access control and upgradeability features. The contract leverages well-audited OpenZeppelin libraries, which enhances its security posture. Key areas of focus include access control for minting and upgrades, the inherent risks of the `permit` function, and general upgrade safety considerations.

> **Final Recommendation:** It is recommended to maintain strict operational security for the multisig wallet controlling administrative roles, especially for upgrade and minting permissions. Regular audits of any new implementation logic prior to upgrades are crucial to prevent the introduction of new vulnerabilities. Users should be educated on the front-running risks associated with the `permit` function to ensure they understand the implications of off-chain signed approvals.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 7/10 | Low | The technical architecture appears sound, relying heavily on battle-tested OpenZeppelin upgradeable contracts and libraries (7.1 Architecture). This approach significantly reduces the likelihood of… |
| **Governance / Economics** | 1/10 | High | The contract exhibits centralized control over critical functions such as token minting and contract upgrades (7.3 Access Control, 7.5 Governance). This control is managed by a 4-of-6 multisig… |
| **Upgrades** | 1/10 | High | The contract utilizes the UUPS proxy pattern, a robust and widely adopted standard for upgradeability (7.7 Upgrades). This pattern allows for future enhancements and bug fixes without deploying a new… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Uups |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 93.8% |
| **Top-3 Unlocked** | ⚠️ 96.3% |

## Security Findings

_🟡 1 Medium · 🟢 1 Low · ⚪ 3 Informational_

### `M-01` — Centralized Control over Token Operations and Upgrades  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `AukiToken` contract, as inferred from the provided interfaces and metadata, likely implements `AccessControlUpgradeable` and `UUPSUpgradeable`. This implies that critical functions such as token minting (given `has_mint: true`) and contract upgrades are controlled by specific roles (e.g., `MINTER_ROLE`, `DEFAULT_ADMIN_ROLE`). While the prefill indicates these roles are managed by a 4-of-6 multisig wallet, which significantly mitigates the risk of a single point of failure, it still represents a centralized authority. Compromise of the multisig signers could lead to unauthorized minting, malicious upgrades, or othe

**Recommendation:** Ensure robust operational security practices for the multisig wallet and its signers. Consider implementing time-locks for critical administrative actions (e.g., upgrades, role changes) to provide a window for community review or emergency intervention. Explore decentralized governance mechanisms for future iterations if applicable to further distribute control.


### `L-01` — Standard `permit` Function Front-Running Risk  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The presence of `IERC20PermitUpgradeable` indicates the token supports the `permit` function, allowing users to approve token spending off-chain via signed messages. While convenient, this mechanism is susceptible to front-running. An attacker monitoring the mempool could observe a legitimate `permit` transaction, then submit their own transaction with a higher gas fee to approve and spend the tokens before the original transaction is confirmed. This is an inherent characteristic of the `permit` design and not a flaw in the implementation itself.

**Recommendation:** Educate users about the potential for front-running when using the `permit` function. Advise them to be cautious when broadcasting signed messages and consider using services that protect against front-running if available. Implementations can also consider adding a `deadline` parameter to `permit` calls to limit the window of vulnerability.


### `I-01` — Reliance on OpenZeppelin Upgradeable Contracts  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract heavily relies on OpenZeppelin's battle-tested upgradeable contracts and libraries (e.g., `AddressUpgradeable`, `CountersUpgradeable`, `StorageSlotUpgradeable`, `AccessControlUpgradeable`, `ERC20Upgradeable`, `UUPSUpgradeable`). This is a significant strength, as these libraries are widely used and have undergone extensive audits and community review. However, any future vulnerabilities discovered in these underlying libraries could potentially affect this contract.

**Recommendation:** Stay informed about security updates and advisories from OpenZeppelin. Regularly review the dependencies for any reported vulnerabilities and be prepared to upgrade the implementation if critical issues are identified in the underlying libraries.


### `I-02` — Potential for Storage Collisions in Custom Upgrades  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). While OpenZeppelin's UUPS pattern is designed to prevent storage collisions, any custom storage variables added to the `AukiToken` implementation or incorrect inheritance order in future upgrades could potentially lead to storage collisions. This occurs when a variable in a new implementation occupies the same storage slot as a different variable in the previous implementation, leading to data corruption or unexpected behavior.

**Recommendation:** Adhere strictly to OpenZeppelin's storage layout guidelines for upgradeable contracts. When adding new state variables in future upgrades, always append them to the end of the contract's storage layout. Thoroughly test all upgrade paths in a staging environment to identify and prevent potential storage collisions before deploying to production.


### `I-03` — Re-initialization Attack Vector  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). UUPS proxy implementations are generally susceptible to re-initialization attacks if the `initialize` function is not properly protected. An attacker could call `initialize` again on the implementation contract (if not properly disabled) or on the proxy itself, potentially resetting critical state variables or re-assigning administrative roles. OpenZeppelin's `UUPSUpgradeable` typically includes mechanisms like `_disableInitializers` in the constructor and the `initializer` modifier to prevent this.

**Recommendation:** Ensure that the `initialize` function in the `AukiToken` implementation is protected by the `initializer` modifier and that `_disableInitializers()` is called in the constructor of the implementation contract to prevent direct calls to `initialize` on the implementation itself. Verify that the proxy's `initialize` function can only be called once.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xf956...5df4`](https://basescan.org/address/0xf9569cfb8fd265e91aa478d86ae8c78b8af55df4) |
| **Network** | Base |
| **Price** | $0.008462 |
| **24h Volume** | $71.5K |
| **Liquidity** | $464.4K |
| **Volume / Liquidity** | 0.2× |
| **Token Age** | 2y |
| **Top-10 Holders** | 82.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 133 buys / 135 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0x2fa9d6085c91151200e61a3e627d35001772c0d1)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/auki-token-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-23*
