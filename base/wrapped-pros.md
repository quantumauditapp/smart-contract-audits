---
token: Wrapped PROS
ticker: PROS
network: base
risk_score: 77
status: critical
date: 2026-07-24
---

# Wrapped PROS (PROS) — Smart Contract Security Analysis | Base

> **Risk Score: 77/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/wrapped-pros-base)

---

## Audit Summary

The BurnMintERC20 contract implements a standard ERC20 token with additional minting and burning capabilities, managed through OpenZeppelin's AccessControl. The contract leverages well-audited libraries and includes checks against common pitfalls like transfers to `address(this)`. The primary risks identified are related to the centralized control of token supply and administrative roles by the `DEFAULT_ADMIN_ROLE`, which can significantly impact the token's economic stability and governance.

> **Final Recommendation:** It is highly recommended to implement robust multi-signature governance for the `DEFAULT_ADMIN_ROLE` to mitigate the risks associated with centralized control over token supply and critical administrative functions. Consider integrating a time-lock mechanism for sensitive operations, such as granting or revoking `MINTER_ROLE` or `BURNER_ROLE`, to provide a window for community review and intervention. Additionally, clearly document the intended purpose and operational procedures for the `CCIPAdmin` role, especially concerning its interaction with external systems.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract demonstrates strong technical foundations (7.2 Code Security) by inheriting from battle-tested OpenZeppelin contracts like ERC20, ERC20Burnable, and AccessControl. It correctly… |
| **Governance / Economics** | 1/10 | High | The contract's economic model (7.4 Economic) benefits from an optional `maxSupply` limit, which can prevent unbounded inflation if configured. However, the `DEFAULT_ADMIN_ROLE` holds significant… |
| **Upgrades** | 3/10 | High | The BurnMintERC20 contract is implemented as a standard, non-upgradeable token (7.7 Upgrades). This design choice eliminates the complexities and potential risks associated with upgradeable proxy… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `H-01` — Centralized Control of Token Supply  *(Severity: High · Status: Unresolved)*

The `DEFAULT_ADMIN_ROLE` has complete authority to grant and revoke `MINTER_ROLE` and `BURNER_ROLE`. This means a single entity or a small group controlling the `DEFAULT_ADMIN_ROLE` can arbitrarily increase or decrease the token's total supply (up to `maxSupply`), significantly impacting the token's economic stability and value. This represents a high centralization risk for the token's economic model (7.3 Access Control, 7.4 Economic).

**Recommendation:** Implement a multi-signature wallet or a decentralized autonomous organization (DAO) to control the `DEFAULT_ADMIN_ROLE`. Consider adding a time-lock for sensitive operations like granting/revoking roles to allow for community oversight and reaction time.


### `M-01` — Centralized CCIPAdmin Role Management  *(Severity: Medium · Status: Unresolved)*

The `s_ccipAdmin` address, intended for external Chainlink CCIP integration, can be set by the `DEFAULT_ADMIN_ROLE` via `setCCIPAdmin`. While this contract does not directly use `s_ccipAdmin` for critical token operations, its centralized control by a single address (the `DEFAULT_ADMIN_ROLE`) could pose a risk to external systems relying on this role if the `DEFAULT_ADMIN_ROLE`'s private key is compromised (7.3 Access Control, 7.6 External).

**Recommendation:** Evaluate the criticality of the `CCIPAdmin` role in external systems. If it holds significant power, consider applying similar multi-signature or time-lock controls to the `setCCIPAdmin` function as recommended for other administrative roles.


### `L-01` — Immutable Decimals Design Choice  *(Severity: Low · Status: Unresolved)*

The token's `decimals` property is set as an immutable variable (`i_decimals`) in the constructor and cannot be changed after deployment. While this ensures consistency and prevents unexpected changes, it means the token's precision is permanently fixed. This might be a limitation if future protocol requirements or ecosystem standards necessitate a change in decimal precision (7.1 Architecture).

**Recommendation:** This is a design choice and not a vulnerability. Ensure that the chosen decimal precision (`i_decimals`) is suitable for all current and foreseeable use cases of the token. No code change is strictly required unless future flexibility is desired.


### `I-01` — Lack of Explicit Admin Role Renouncement Function  *(Severity: Informational · Status: Unresolved)*

The contract relies on the inherited `AccessControl.renounceRole` function for the `DEFAULT_ADMIN_ROLE` to potentially relinquish its administrative powers. However, there is no explicit function within `BurnMintERC20` to facilitate or encourage this. Explicitly exposing or documenting a path for the `DEFAULT_ADMIN_ROLE` to renounce itself could be a step towards decentralization post-deployment (7.5 Governance, 7.8 Operations).

**Recommendation:** Consider adding a public function that calls `renounceRole(DEFAULT_ADMIN_ROLE, msg.sender)` to provide a clear and explicit path for the deployer to renounce the admin role, if decentralization is a future goal. Alternatively, ensure this process is clearly documented.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x8b7d...9832`](https://basescan.org/address/0x8b7dde054be9d180c1be7fae0874697374a49832) |
| **Network** | Base |
| **Price** | $0.3889 |
| **24h Volume** | $916.6K |
| **Liquidity** | $673.7K |
| **Volume / Liquidity** | 1.4× |
| **Token Age** | 1y |
| **Top-10 Holders** | 93.5% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 7821 buys / 8020 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Frequently Asked Questions

### Is Wrapped PROS a scam?

Based on automated analysis, Wrapped PROS scores 69/100 (High Risk) on our risk scale. No honeypot was detected, but always verify independently before investing.

### Is Wrapped PROS safe to buy?

Our scanner flagged a risk score of 69/100. Ownership has not been renounced, which is a risk factor. DYOR before purchasing any token.

### Has Wrapped PROS been audited?

The contract has not been verified on-chain. Verification is not the same as a full security audit. Use Quantum Audit's free tool to run a deeper analysis of the contract code.

## Sources

- [View on DexScreener](https://dexscreener.com/base/0x8a8e4170c09074b109352190d47e54d7c1f61e4e)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/wrapped-pros-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-07-24*
