---
token: BOB
ticker: BOB
network: bsc
risk_score: 69
status: high
date: 2026-08-31
---

# BOB (BOB) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 69/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/bob-bsc)

---

## Audit Summary

The BobToken contract is an upgradeable ERC-20 token utilizing OpenZeppelin's UUPS, Ownable, ERC20Permit, ERC20Burnable, and AccessControl standards. The audit identified a High severity issue related to broken custom role management functions, which are unusable as implemented. Additionally, a Medium severity concern was noted regarding the centralized control over critical roles by the DEFAULT_ADMIN_ROLE, although mitigated by a multisig owner. Overall, the contract demonstrates good adherence to OpenZeppelin best practices for upgradeability and token functionality, but requires attention to the identified access control and role management issues.

> **Final Recommendation:** Prioritize resolving the High severity issue related to the broken role management functions to ensure proper control over minting and burning capabilities. Carefully consider the implications of the centralized control held by the `DEFAULT_ADMIN_ROLE` and explore options for further decentralization or timelocks for critical operations if the project's roadmap requires it. Review the necessity and implications of the `useNonce` function's external exposure. Ensure comprehensive testing of all access control mechanisms and upgrade paths.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract leverages well-vetted OpenZeppelin upgradeable libraries for its ERC-20, burnable, permit, and access control functionalities (7.2 Code Security). The architecture is standard for an… |
| **Governance / Economics** | 3/10 | High | The economic model includes a fixed maximum supply (`i_maxSupply`) for the token, which provides predictability but limits flexibility without an upgrade (7.4 Economic). Governance relies on… |
| **Upgrades** | 1/10 | High | The contract correctly implements the UUPS upgradeability pattern using OpenZeppelin's `UUPSUpgradeable` (7.7 Upgrades). The `_authorizeUpgrade` function is restricted to `onlyOwner`, ensuring that… |

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

_🟡 2 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `M-01` — Centralized Control over Minting/Burning and CCIP Admin  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `DEFAULT_ADMIN_ROLE` holds significant power within the contract. This role can grant/revoke `MINTER_ROLE` and `BURNER_ROLE`, effectively controlling the token's supply dynamics (up to `i_maxSupply`), and can also set the `s_ccipAdmin` address. While the `initialOwner` (assigned `DEFAULT_ADMIN_ROLE`) is a multisig, this still represents a single point of control for these critical functions. A compromise of the multisig could lead to unauthorized token inflation or manipulation of the CCIP admin address.

**Recommendation:** Consider implementing further decentralization or introducing a timelock mechanism for critical operations such as granting/revoking `MINTER_ROLE` or `BURNER_ROLE`, or changing the `s_ccipAdmin`. This would provide a delay for users to react to malicious actions and reduce the immediate impact of a multisig compromise.


### `M-02` — Broken Role Management Functions (`grantMintAndBurnRoles`, `revokeMintAndBurnRoles`)  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `grantMintAndBurnRoles` and `revokeMintAndBurnRoles` functions are intended to manage `MINTER_ROLE` and `BURNER_ROLE`. However, they lack explicit access control (e.g., `onlyRole(DEFAULT_ADMIN_ROLE)`). When these functions are called, they internally invoke `grantRole` or `revokeRole`. Since `grantRole` and `revokeRole` are protected by `onlyRole(getRoleAdmin(role))`, and the `msg.sender` for the internal call is the contract itself (`address(this)`), which does not hold `DEFAULT_ADMIN_ROLE`, these functions will always revert. This renders the custom role management functions unusable, requiring `DEFAULT_ADMIN_ROL

**Recommendation:** Add `onlyRole(DEFAULT_ADMIN_ROLE)` to both `grantMintAndBurnRoles` and `revokeMintAndBurnRoles` functions. This will ensure that only authorized administrators can call these functions, and the internal calls to `grantRole`/`revokeRole` will then be correctly executed with the `msg.sender` being the authorized administrator.


### `L-01` — Fixed Max Supply Value  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `i_maxSupply` is hardcoded in the `initialize` function to `10,000,000,000 * 10**decimals()`. While this provides a clear and immutable supply cap, it means the maximum supply cannot be adjusted without a contract upgrade. If future protocol needs or market conditions require a different supply cap, an upgrade would be necessary, which might not always be desirable or feasible.

**Recommendation:** If flexibility in the maximum supply is desired, consider making `i_maxSupply` configurable by a privileged role (e.g., `DEFAULT_ADMIN_ROLE`) or through a governance mechanism. If the intention is for the maximum supply to be permanently fixed, no change is strictly necessary, but this design choice should be explicitly documented.


### `I-01` — External `useNonce` Function Exposure  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `useNonce()` function is an external wrapper around `_useNonce(msg.sender)`. While it doesn't pose a direct vulnerability, `_useNonce` is typically an internal function used by `ERC20Permit`'s `_permit` and `_approve` functions to prevent replay attacks. Exposing this internal mechanism directly via an external function might lead to confusion or unintended usage if its purpose is not clearly understood or documented.

**Recommendation:** Review if the `useNonce()` function is truly necessary for external calls. If its functionality is only required internally by the `ERC20Permit` mechanism, consider removing the external wrapper. If it serves a specific external purpose, ensure its functionality and intended use cases are thoroughly documented.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x52b5...b7e7`](https://bscscan.com/address/0x52b5fb4b0f6572b8c44d0251cc224513ac5eb7e7) |
| **Network** | BNB Chain |
| **Price** | $0.004826 |
| **24h Volume** | $84.9K |
| **Liquidity** | $449.5K |
| **Volume / Liquidity** | 0.2× |
| **Token Age** | 9mo |
| **Top-10 Holders** | 94.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2933 buys / 3606 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x1d11060dce19cbc2650f6a84f728fc0e54cf7faa)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/bob-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-31*
