---
token: Tether USD
ticker: USDT
network: base
risk_score: 50
status: high
date: 2026-07-23
---

# Tether USD (USDT) — Smart Contract Security Analysis | Base

> **Risk Score: 50/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/tether-usd-base)

---

## Audit Summary

The audited contract is an ERC-20 token implementation, leveraging OpenZeppelin Contracts v3.4.1 for standard functionalities like `ERC20`, `Ownable`, `Pausable`, and `SafeMath`. The contract exhibits robust technical security due to the use of battle-tested libraries, including proper handling of integer overflows/underflows. However, it features a highly centralized control model, where an owner can mint, burn, and pause operations, which introduces significant governance and economic risks. The standard ERC-20 `approve` race condition is present, though mitigated by `increaseAllowance` and `decreaseAllowance` functions.

> **Final Recommendation:** It is recommended to carefully manage the private keys associated with the `_owner` and `_pauser` roles due to their extensive control over the token's supply and operational status. Consider implementing a multi-signature wallet for these critical roles to enhance security and decentralization. For users, it is advisable to prefer `increaseAllowance` and `decreaseAllowance` over the direct `approve` function to mitigate front-running risks.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 5/10 | Medium | The contract demonstrates good technical security (7.2 Code Security) by utilizing OpenZeppelin Contracts v3.4.1, which include `SafeMath` for all arithmetic operations, effectively preventing… |
| **Governance / Economics** | 2/10 | High | The contract exhibits a high degree of centralization (7.3 Access Control, 7.4 Economic, 7.5 Governance). The `_owner` role has extensive privileges, including the ability to `mint` and `burn`… |
| **Upgrades** | 5/10 | Medium | The contract is not designed with an upgrade mechanism (7.7 Upgrades), meaning its logic is immutable once deployed. This eliminates upgrade-related risks such as proxy misconfigurations or logic… |

## Security Findings

_🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `H-01` — Extensive Centralized Control  *(Severity: High · Status: Unresolved)*

The `_owner` possesses significant control, including the ability to `mint` and `burn` tokens, directly influencing the total supply and token value. Additionally, the `_pauser` can `pause` and `unpause` all core token operations (transfers, approvals, minting, burning), leading to potential denial of service for users. This design introduces high trust assumptions and a single point of failure (7.3 Access Control, 7.4 Economic, 7.8 Operations).

**Recommendation:** Implement a multi-signature wallet for the `_owner` and `_pauser` roles to distribute control and reduce the risk of a single point of compromise. Clearly communicate the extent of centralized control to users and stakeholders.


### `M-01` — ERC-20 `approve` Race Condition  *(Severity: Medium · Status: Unresolved)*

The standard `approve` function is susceptible to a known front-running attack. If a user approves an amount, then approves a different amount without first setting the allowance to zero, a malicious actor could potentially spend both the old and new allowances. While `increaseAllowance` and `decreaseAllowance` are provided as safer alternatives, the direct `approve` function remains (7.2 Code Security).

**Recommendation:** Educate users to primarily use `increaseAllowance` and `decreaseAllowance` instead of directly calling `approve` when modifying existing allowances. If `approve` must be used, advise users to first set the allowance to zero before setting a new value.


### `L-01` — Immutability of Core Token Parameters  *(Severity: Low · Status: Unresolved)*

The token's name, symbol, and decimals are set during construction and cannot be modified post-deployment. While standard for ERC-20 tokens, this means any initial misconfiguration of these parameters would require a new contract deployment (7.1 Architecture).

**Recommendation:** Ensure thorough verification of all constructor parameters, especially token name, symbol, and decimals, before deployment to prevent irreversible misconfigurations.


### `I-01` — Use of OpenZeppelin Contracts v3.4.1  *(Severity: Informational · Status: Unresolved)*

The contract leverages well-audited OpenZeppelin libraries (Context, IERC20, SafeMath, ERC20, Ownable, Pausable) version 3.4.1. This significantly reduces the risk of common vulnerabilities by using battle-tested code, but means the contract inherits any potential, albeit unlikely, issues within these specific library versions (7.6 External).

**Recommendation:** Regularly monitor OpenZeppelin security advisories for the specific versions used. Consider upgrading to newer, actively maintained versions of OpenZeppelin Contracts if feasible and beneficial for new deployments, as they often include further optimizations and security enhancements.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xfde4...9bb2`](https://basescan.org/address/0xfde4c96c8593536e31f229ea8f37b2ada2699bb2) |
| **Network** | Base |
| **Price** | $0.9989 |
| **24h Volume** | $5.73M |
| **Liquidity** | $1.74M |
| **Volume / Liquidity** | 3.3× |
| **Token Age** | 1y |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 5354 buys / 1379 sells |

## Security Flags (1/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ❌ Fail |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ⚠️ Unknown |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ❌ | Source code is **not verified** — contract logic is opaque. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/base/0xa41bc0affba7fd420d186b84899d7ab2ac57fcd1)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/tether-usd-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-07-23*
