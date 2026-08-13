---
token: Bless Token
ticker: BLESS
network: bsc
risk_score: 93
status: critical
date: 2026-08-13
---

# Bless Token (BLESS) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 93/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/bless-token-bsc)

---

## Audit Summary

The DeBridgeToken contract serves as an upgradeable ERC-20 token implementation, utilizing OpenZeppelin's upgradeable contracts and access control. The contract features centralized minting, pausing, and administrative control, which introduces significant economic and governance risks. While the code adheres to OpenZeppelin best practices for upgradeability and ERC-20 functionality, the extensive power vested in specific roles (Admin, Minter, Pauser) represents a high degree of centralization. Key management for these roles is critical to prevent single points of failure and potential misuse of power, which could impact token supply, transferability, and identity.

> **Final Recommendation:** It is strongly recommended to implement robust multi-signature governance for all critical roles, especially `DEFAULT_ADMIN_ROLE`, `MINTER_ROLE`, and `PAUSER_ROLE`, to mitigate the risks associated with centralized control and single points of failure. Clear documentation and communication regarding the unusual behavior of the `burn` function and the implications of the `updateName` function should be provided to users and integrators. Regular security reviews and monitoring of privileged addresses are essential to maintain the integrity and security of the DeBridgeToken.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 4/10 | Medium | The DeBridgeToken contract is built upon battle-tested OpenZeppelin upgradeable libraries, ensuring a solid foundation for ERC-20 functionality, access control, and pausability (7.2 Code Security).… |
| **Governance / Economics** | 1/10 | High | The contract exhibits a high degree of centralization, with the `DEFAULT_ADMIN_ROLE` having the power to grant/revoke `MINTER_ROLE` and `PAUSER_ROLE`, effectively controlling token supply and… |
| **Upgrades** | 1/10 | High | The contract utilizes OpenZeppelin's `Initializable` and upgradeable patterns, correctly managing storage slots and initialization to prevent common upgrade-related issues (7.7 Upgrades). As a beacon… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Beacon |
| **Implementation** | ✅ Verified source |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 59.8% |
| **Top-3 Unlocked** | ⚠️ 98.1% |

## Security Findings

_🟠 1 High · 🟡 2 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `H-01` — Centralized Control of Critical Functions (Minting, Pausing, Admin)  *(Severity: High · Status: Unresolved)*

The contract grants extensive power to specific roles: `DEFAULT_ADMIN_ROLE` can manage all other roles, `MINTER_ROLE` can arbitrarily increase token supply via `mint`, and `PAUSER_ROLE` can halt all token transfers via `pause`/`unpause`. This high degree of centralization means that a compromise or malicious action by an address holding these roles could severely impact the token's integrity, value, and usability. The `DEFAULT_ADMIN_ROLE` effectively controls the entire token's lifecycle and economic parameters.

**Recommendation:** Implement a robust multi-signature wallet or a decentralized governance mechanism for the `DEFAULT_ADMIN_ROLE`, `MINTER_ROLE`, and `PAUSER_ROLE`. This distributes control and requires multiple approvals for critical operations, significantly reducing the risk of a single point of failure or malicious insider actions. Clearly document the responsibilities and operational procedures for each role.


### `M-01` — `updateName` Function Allows Token Identity Change  *(Severity: Medium · Status: Unresolved)*

The `updateName` function, callable only by the `DEFAULT_ADMIN_ROLE`, allows the token's name and symbol to be changed post-deployment. While the `DOMAIN_SEPARATOR` is correctly re-calculated, this capability could lead to user confusion, misrepresentation on exchanges, or potential trust issues if not managed with extreme transparency and community consensus. Frequent or unannounced changes to a token's identity can erode user confidence.

**Recommendation:** Consider if the ability to change the token's name and symbol is truly necessary post-deployment. If it is, ensure that any changes are communicated transparently and well in advance to all stakeholders, including exchanges and users. Implement a time-lock or a governance vote for such critical changes to provide a window for review and prevent immediate, unilateral alterations.


### `M-02` — Unusual `burn` Function Implementation  *(Severity: Medium · Status: Unresolved)*

The `burn` function is restricted to `onlyMinter` and allows the minter to burn `msg.sender`'s (i.e., their own) tokens. This deviates from the common ERC-20 `burn` pattern, where any token holder can burn their own tokens without requiring a special role. This design choice limits the utility of the burn function and might lead to confusion or unmet expectations for users accustomed to standard ERC-20 token behavior.

**Recommendation:** Clarify the intended purpose of the `burn` function. If the goal is to allow any token holder to burn their own tokens, remove the `onlyMinter` modifier. If the intent is specifically for minters to manage their own token holdings through burning, document this behavior clearly to avoid user confusion. Consider adding a separate `burnFrom` function if minters are intended to burn tokens from other addresses.


### `L-01` — Single Point of Failure for Privileged Roles  *(Severity: Low · Status: Unresolved)*

If the addresses assigned to `DEFAULT_ADMIN_ROLE`, `MINTER_ROLE`, or `PAUSER_ROLE` are single Externally Owned Accounts (EOAs), they represent single points of failure. A compromise of any of these EOAs (e.g., private key theft) would grant an attacker full control over the respective privileged functions, potentially leading to severe consequences for the token and its holders.

**Recommendation:** Ensure that all privileged roles (`DEFAULT_ADMIN_ROLE`, `MINTER_ROLE`, `PAUSER_ROLE`) are assigned to multi-signature wallets (e.g., Gnosis Safe) rather than single EOAs. This significantly enhances security by requiring multiple approvals for any action, making it much harder for an attacker to gain full control.


### `I-01` — EIP-712 `permit` Function Susceptible to Front-running  *(Severity: Informational · Status: Unresolved)*

The `permit` function, while correctly implemented with `deadline` and `nonces` to prevent replay attacks, is inherently susceptible to front-running. A malicious actor observing a signed `permit` message off-chain could submit the transaction with a higher gas price before the legitimate `spender`, effectively 'stealing' the approval. This is a general characteristic of EIP-712 `permit` and not a flaw in this specific implementation.

**Recommendation:** Educate users about the potential for front-running when using the `permit` function. Advise them to be cautious when sharing signed messages and to consider using transaction privacy services if available and necessary for highly sensitive approvals. This risk is generally mitigated by the `deadline` parameter, but users should be aware.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x7c82...e11f`](https://bscscan.com/address/0x7c8217517ed4711fe2deccdfeffe8d906b9ae11f) |
| **Network** | BNB Chain |
| **Price** | $0.01019 |
| **24h Volume** | $2.09M |
| **Liquidity** | $229.4K |
| **Volume / Liquidity** | 9.1× |
| **Token Age** | 10mo |
| **Top-10 Holders** | 92.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 17685 buys / 19451 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x49986efbeedea3ab962ca95caf86919860ecc9db)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/bless-token-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-13*
