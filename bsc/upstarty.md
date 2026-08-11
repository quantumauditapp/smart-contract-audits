---
token: Upstarty
ticker: UPY
network: bsc
risk_score: 66
status: high
date: 2026-08-11
---

# Upstarty (UPY) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 66/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/upstarty-bsc)

---

## Audit Summary

The Upstarty token contract implements a standard ERC20 token with burnable and pausable functionalities, largely based on OpenZeppelin's secure patterns. The code demonstrates good practices such as custom error handling and appropriate use of unchecked arithmetic. However, a significant concern is the lack of explicit access control for the critical `_pause()` and `_unpause()` functions within the `Pausable` abstract contract, which must be carefully addressed by the inheriting contract to prevent unauthorized control over token transfers. The centralized nature of the pausing mechanism also introduces a governance and economic risk.

> **Final Recommendation:** It is crucial to implement robust access control for the `_pause()` and `_unpause()` functions in the inheriting contract to prevent unauthorized pausing or unpausing of token transfers. Consider using a well-tested access control mechanism like OpenZeppelin's `Ownable` or `AccessControl` for these critical functions. Additionally, carefully evaluate the implications of the centralized `Pausable` control on the token's economic and governance model, and consider decentralizing this control through a multi-signature wallet or a governance mechanism if appropriate for the project's risk profile.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract implements a standard ERC20 token with burnable and pausable features, largely following OpenZeppelin patterns. It utilizes custom error types for improved clarity and gas efficiency.… |
| **Governance / Economics** | 1/10 | High | The `Pausable` functionality provides an emergency stop mechanism, which can be beneficial for mitigating certain attack vectors or operational issues (7.8 Operations). However, this introduces a… |
| **Upgrades** | 6/10 | Medium | The provided code does not include any proxy or upgradeability patterns (7.7 Upgrades). It is a standard, non-upgradeable contract implementation. Therefore, there are no inherent upgrade safety… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 56.4% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 1 Medium · ⚪ 2 Informational_

### `H-01` — Missing Access Control for Pausable Functions  *(Severity: High · Status: Unresolved)*

The `Pausable` abstract contract defines `_pause()` and `_unpause()` as `internal virtual` functions without any inherent access control. While this design allows inheriting contracts to implement their own access control, it creates a high-risk vulnerability if the inheriting contract exposes these functions publicly (e.g., via a `pause()` or `unpause()` external function) without proper authorization checks. An attacker could then halt all token transfers, severely impacting the token's utility and user trust. This is a critical design consideration for any contract inheriting `Pausable` (7.3 Access Control).

**Recommendation:** The inheriting contract (e.g., 'Upstarty') must implement robust access control for any public or external functions that call `_pause()` and `_unpause()`. It is highly recommended to use a battle-tested access control mechanism such as OpenZeppelin's `Ownable` or `AccessControl` to restrict these functions to authorized addresses only.


### `M-01` — Centralization Risk of Pausable Functionality  *(Severity: Medium · Status: Unresolved)*

The `Pausable` contract allows for the complete halting of all token transfers and related operations. While this feature can be valuable for emergency situations (e.g., mitigating a severe vulnerability), it introduces a significant centralization risk. The entity or address that controls the `_pause()` and `_unpause()` functions holds considerable power over the token's functionality, potentially leading to censorship, manipulation, or single point of failure (7.4 Economic, 7.5 Governance).

**Recommendation:** Carefully consider the implications of centralized control over the `Pausable` functionality. If the project aims for decentralization, explore options such as multi-signature wallets for controlling the pause mechanism, or integrate it into a broader governance system where decisions are made by token holders or a decentralized autonomous organization (DAO). Clearly document the conditions under which pausing may occur and the process for unpausing.


### `I-01` — Safe Use of Unchecked Arithmetic  *(Severity: Informational · Status: Resolved)*

The contract utilizes `unchecked` blocks for arithmetic operations within the `_update` function, specifically for `_balances[from] = fromBalance - value;`, `_balances[to] += value;`, and `_totalSupply -= value;`. In Solidity 0.8.x, arithmetic operations revert on overflow/underflow by default. The use of `unchecked` here is safe and gas-efficient because preceding logic (e.g., `if (fromBalance < value)`) ensures that underflow will not occur for subtractions, and additions are generally safe within `uint256` limits for typical token values (7.2 Code Security).

**Recommendation:** No action required. The use of `unchecked` blocks is appropriate and correctly implemented in this context, contributing to gas efficiency without compromising security.


### `I-02` — Abstract Contract Requires Inheritance  *(Severity: Informational · Status: Resolved)*

The provided code consists of several abstract contracts (`Context`, `ERC20`, `Pausable`, `ERC20Burnable`, `ERC20Pausable`). These contracts cannot be deployed directly and are intended to be inherited by a concrete contract (e.g., 'Upstarty'). The final deployed contract will combine the functionalities defined here with any additional logic implemented in the inheriting contract (7.1 Architecture).

**Recommendation:** No direct action is required for the abstract contracts themselves. However, it is crucial to ensure that the inheriting contract correctly implements all necessary functionalities, including proper constructor arguments, access control for critical functions (as noted in H-01), and any specific tokenomics or business logic.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xb849...3466`](https://bscscan.com/address/0xb849c4d843769d42812fb600b1bcc8a6ba843466) |
| **Network** | BNB Chain |
| **Price** | $0.09946 |
| **24h Volume** | $32.4K |
| **Liquidity** | $117.6K |
| **Volume / Liquidity** | 0.3× |
| **Token Age** | 1y |
| **Top-10 Holders** | 92.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 112 buys / 93 sells |

## Security Flags (4/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x90b2ffd887bab701ef39ba482a67fbee125bf465)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/upstarty-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-11*
