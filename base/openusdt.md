---
token: OpenUSDT
ticker: OUSDT
network: base
risk_score: 50
status: high
date: 2026-08-13
---

# OpenUSDT (OUSDT) — Smart Contract Security Analysis | Base

> **Risk Score: 50/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/openusdt-base)

---

## Audit Summary

The XERC20 contract, an upgradeable ERC-20 token, was audited for security vulnerabilities. A critical vulnerability was identified where the `mint` function is publicly accessible, allowing any caller to create new tokens, leading to uncontrolled supply inflation. Other findings include potential rate limit bypasses, immutability concerns for a critical operational address, and minor issues related to naming conventions and hardcoded values.

> **Final Recommendation:** The primary recommendation is to immediately address the critical vulnerability in the `mint` function by restricting its access to authorized roles only. This is paramount to prevent uncontrolled token inflation and maintain the token's economic integrity. Additionally, review the rate limiting mechanism to ensure it effectively controls overall token supply, especially if multiple actors can trigger minting. Consider making the `lockbox` address configurable by the owner to allow for future operational flexibility without requiring a full contract upgrade.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 4/10 | Medium | The contract leverages OpenZeppelin's upgradeable ERC20 and Ownable patterns, providing a solid foundation for token functionality and access control (7.2 Code Security). It implements a rate… |
| **Governance / Economics** | 2/10 | High | The contract's ownership is secured by a Timelock with a 24-hour delay, which is a strong governance practice for administrative functions like setting rate limits and adding/removing bridges (7.5… |
| **Upgrades** | 1/10 | High | The contract utilizes the Transparent Upgradeable Proxy pattern, with the proxy admin owned by a Timelock, ensuring a secure and controlled upgrade path (7.7 Upgrades). The `initialize` function is… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Transparent |
| **Admin** | OZ ProxyAdmin → Timelock |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🔴 1 Critical · 🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `C-01` — Public `mint` function allows arbitrary token creation  *(Severity: Critical · Status: Unresolved)*

The `mint(address _user, uint256 _amount)` function is declared `public`, allowing any external caller to mint new tokens to any specified address. This bypasses typical access control mechanisms for token creation, leading to uncontrolled inflation and potential devaluation of the token. While the `_mintWithCaller` function applies a rate limit based on `msg.sender`, this only limits the rate of minting per individual caller, not the overall ability to inflate the supply.

**Recommendation:** Restrict the `mint` function to authorized roles (e.g., `onlyOwner` or a dedicated minter role) or remove it if minting is only intended via cross-chain mechanisms.


### `H-01` — Rate limit bypass via multiple addresses  *(Severity: High · Status: Unresolved)*

The rate limiting mechanism in `_depleteBuffer` and `_replenishBuffer` is applied per `_caller` address. If the `mint` function remains public, an attacker could use multiple distinct addresses to bypass the individual rate limits, effectively minting a large amount of tokens quickly by distributing the minting operations across many accounts. This undermines the intended purpose of the rate limits for controlling overall token supply.

**Recommendation:** If the `mint` function is intended to be public (which is highly discouraged), consider implementing a global rate limit in addition to or instead of the per-caller rate limit, or restrict the `mint` function to a single, trusted entity.


### `M-01` — Immutability of `lockbox` address  *(Severity: Medium · Status: Unresolved)*

The `lockbox` address is declared `immutable` and set in the constructor. This address is used to bypass rate limits for internal minting/burning operations. If the `lockbox` address needs to be changed in the future due to compromise, operational changes, or system evolution, it cannot be updated without a full contract upgrade, which is a more complex and risky operation than a simple parameter change.

**Recommendation:** Re-evaluate the necessity of `lockbox` being `immutable`. If it represents a critical operational address that might need to change, consider making it a mutable `onlyOwner` configurable variable.


### `L-01` — Hardcoded `decimals` value  *(Severity: Low · Status: Unresolved)*

The `decimals()` function is hardcoded to return `6`. While this is a valid design choice, it means the token will always have 6 decimal places. If there's a future need to change the decimal precision (e.g., for integration with other systems that expect a different standard like 18), it would require a contract upgrade.

**Recommendation:** Document this design choice clearly. If flexibility is desired, consider making `decimals` an `immutable` variable set in the constructor or an `onlyOwner` configurable variable, though changing decimals for an existing token is generally not recommended due to ecosystem impact.


### `I-01` — Ambiguous `burn` function naming  *(Severity: Informational · Status: Unresolved)*

The `burn(address _user, uint256 _amount)` function is public and allows `msg.sender` to burn tokens from `_user` if `msg.sender` has an allowance from `_user`. This behavior is typically associated with a `burnFrom` function in ERC20 standards, while a `burn` function usually implies burning tokens owned by `msg.sender`. The current naming might lead to confusion for integrators or users.

**Recommendation:** Rename the function to `burnFrom(address _user, uint256 _amount)` to align with common ERC20 naming conventions if it's intended to allow burning on behalf of others. If it's only intended for users to burn their own tokens, then the allowance check should be removed, and `_user` should be `msg.sender`.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x1217...e189`](https://basescan.org/address/0x1217bfe6c773eec6cc4a38b5dc45b92292b6e189) |
| **Network** | Base |
| **Price** | $0.9993 |
| **24h Volume** | $162.1K |
| **Liquidity** | $136.2K |
| **Volume / Liquidity** | 1.2× |
| **Token Age** | 1y |
| **Top-10 Holders** | 93.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 251 buys / 287 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0x4858ba5a92a23de1b2dbb3509b01d0a9f0e0756a)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/openusdt-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-13*
