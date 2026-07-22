---
token: SKYAI
ticker: SKYAI
network: bsc
risk_score: 42
status: medium
date: 2026-07-22
---

# SKYAI (SKYAI) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 42/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/skyai-bsc)

---

## Audit Summary

This audit covers the provided Solidity source code, which includes OpenZeppelin's `Context.sol` and a truncated `ERC20.sol`. The analysis is limited as the full `ERC20.sol` implementation and any derived `SKYAIToken` contract logic were not provided. Based on the available OpenZeppelin base code, the technical risk is low, but the absence of the complete source code for the specific token contract prevents a comprehensive security assessment.

> **Final Recommendation:** It is crucial to provide the complete and final source code for the `SKYAIToken` contract, including any custom logic, minting, burning, or access control mechanisms, to enable a comprehensive security audit. Without the full implementation, potential vulnerabilities specific to the token's unique functionality cannot be identified or assessed. Ensure all custom logic adheres to secure coding practices, especially regarding access control and external interactions.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The provided code utilizes battle-tested OpenZeppelin contracts (7.2 Code Security), which are known for their robust implementation and adherence to best practices. Standard ERC20 functions like… |
| **Governance / Economics** | 3/10 | High | As a standard ERC20 token (7.4 Economic), the contract does not inherently include complex governance mechanisms or economic models beyond basic token transfers and allowances. There are no specific… |
| **Upgrades** | 5/10 | Medium | The provided contract is a direct implementation of ERC20 and is not designed as an upgradeable proxy (7.7 Upgrades). Therefore, upgradeability risks such as storage collisions or incorrect… |

## Security Findings

_🟢 1 Low · ⚪ 2 Informational_

### `L-01` — Allowance Race Condition in `approve()`  *(Severity: Low · Status: Unresolved)*

The standard ERC20 `approve()` function is susceptible to a known front-running vulnerability. If a user approves an allowance for a spender, and then attempts to change that allowance by calling `approve()` again with a new amount, a malicious actor could front-run the second transaction. This could allow the attacker to spend the original allowance, and then also spend the new allowance, effectively doubling the amount they can spend (7.2 Code Security). OpenZeppelin mitigates this by providing `increaseAllowance()` and `decreaseAllowance()` functions, which are safer alternatives.

**Recommendation:** Advise users to primarily use `increaseAllowance()` and `decreaseAllowance()` instead of directly calling `approve()` when modifying existing allowances. If `approve()` must be used, users should first set the allowance to zero before setting a new value, though this still requires two transactions and introduces a small window of vulnerability.


### `I-01` — Incomplete Source Code Provided  *(Severity: Informational · Status: Unresolved)*

The provided source code for the `ERC20.sol` contract is truncated, and the specific `SKYAIToken` contract, which is likely derived from `ERC20`, was not provided. This significantly limits the scope of the audit, as any custom logic, state variables, or function overrides within the complete `ERC20.sol` or `SKYAIToken` contract could not be analyzed for vulnerabilities (7.1 Architecture, 7.2 Code Security).

**Recommendation:** Provide the complete and final source code for all contracts intended for deployment, including the full `ERC20.sol` and the `SKYAIToken` contract, to allow for a comprehensive security assessment.


### `I-02` — Lack of Custom Functionality for Audit  *(Severity: Informational · Status: Unresolved)*

The audit was conducted on a base OpenZeppelin ERC20 implementation. Without the specific `SKYAIToken` contract's code, any custom functionalities such as minting, burning, pausing, fee mechanisms, or specific access control roles (7.3 Access Control, 7.8 Operations) could not be reviewed. This means that potential vulnerabilities related to the unique business logic of `SKYAIToken` are outside the scope of this report.

**Recommendation:** Ensure that any custom logic implemented in the `SKYAIToken` contract is thoroughly reviewed for common vulnerabilities such as reentrancy, access control bypasses, integer overflows/underflows, and logical errors. Consider a separate audit for the full custom implementation.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x92aa...fb10`](https://bscscan.com/address/0x92aa03137385f18539301349dcfc9ebc923ffb10) |
| **Network** | BNB Chain |
| **Price** | $0.0276 |
| **24h Volume** | $543.8K |
| **Liquidity** | $3.86M |
| **Volume / Liquidity** | 0.1× |
| **Token Age** | 1y |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1519 buys / 1212 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ❌ Fail |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ❌ | Source code is **not verified** — contract logic is opaque. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0xbc42145d5a574ede9b8860fca2a49eb7b239efa5)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/skyai-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-07-22*
