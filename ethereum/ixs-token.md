---
token: Ixs Token
ticker: IXS
network: ethereum
risk_score: 35
status: medium
date: 2026-09-02
---

# Ixs Token (IXS) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 35/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/ixs-token-eth)

---

## Audit Summary

The IxsToken contract implements a standard ERC20 token with minting and burning capabilities, utilizing OpenZeppelin's SafeMath and role-based access control for Minter and Pauser functionalities. The code is generally well-structured and follows common patterns. However, significant centralization risks exist due to critical roles being controlled by a single address, and the use of an older Solidity compiler version introduces potential for missing modern security features.

> **Final Recommendation:** It is strongly recommended to implement a multi-signature wallet for managing the `MinterRole` and `PauserRole` to mitigate the risks associated with centralized control. Consider upgrading the Solidity compiler version to a more recent release (e.g., 0.8.x) to benefit from improved security features and gas optimizations. Implement a recovery mechanism for accidentally sent tokens to prevent permanent loss of funds.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract implements a standard ERC20 token with minting and burning capabilities, leveraging OpenZeppelin's `SafeMath` for arithmetic safety (7.2 Code Security). The architecture is modular… |
| **Governance / Economics** | 4/10 | Medium | The token's economic model includes minting and burning, controlled by specific roles. The `MinterRole` and `PauserRole` are critical for token supply management and emergency control (7.4 Economic).… |
| **Upgrades** | 4/10 | Medium | The contract does not incorporate any upgradeability patterns (7.7 Upgrades). This means the contract's logic is immutable once deployed, preventing future bug fixes, feature enhancements, or… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 89.9% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 2 Medium · 🟢 2 Low · ⚪ 2 Informational_

### `M-01` — Lack of Multi-Signature for Critical Operations  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). While the contract implements role-based access control for minting and pausing, the management of these roles (adding/removing minters/pausers) is also controlled by existing minters/pausers. Without a multi-signature wallet or a more robust governance mechanism, a single compromised Minter or Pauser could unilaterally add new malicious role holders or remove legitimate ones, leading to a loss of control.

**Recommendation:** For critical administrative functions, especially those involving role management, consider integrating a multi-signature wallet or a time-locked governance mechanism. This adds an extra layer of security by requiring consensus for sensitive changes.


### `M-02` — Centralization of Minter and Pauser Roles  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `MinterRole` and `PauserRole` are critical roles that grant the ability to mint new tokens (potentially inflating supply) and pause all token transfers, respectively. Both roles are initially assigned to the contract deployer in their respective constructors (`MinterRole` and `PauserRole`). This creates a single point of failure, as a compromise of the deployer's private key would allow an attacker to mint arbitrary tokens or halt all token operations.

**Recommendation:** Implement a multi-signature wallet (e.g., Gnosis Safe) to control the `MinterRole` and `PauserRole`. This would require multiple independent approvals for any sensitive action, significantly reducing the risk of a single point of compromise.


### `L-01` — Outdated Solidity Compiler Version  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract uses Solidity compiler version `^0.5.0`. Newer Solidity versions (e.g., 0.8.x) include significant security enhancements, such as default integer overflow/underflow checks (removing the need for SafeMath in many cases), custom errors for more efficient error handling, and improved gas optimizations. Using an older version might miss out on these benefits and potentially expose the contract to known compiler-related issues that have since been patched.

**Recommendation:** Consider upgrading the Solidity compiler version to a more recent and stable release (e.g., 0.8.x). Thoroughly test the contract after the upgrade to ensure compatibility and correct functionality.


### `L-02` — Missing Emergency Token Recovery Mechanism  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract does not include a function to recover ERC20 tokens or native currency (ETH) that might be accidentally sent to the contract address. If any unsupported tokens or ETH are sent to the contract, they will become permanently locked and inaccessible, leading to a loss of funds.

**Recommendation:** Implement a function, callable only by an authorized address (e.g., a multi-sig wallet), to recover accidentally sent ERC20 tokens and native currency. This function should allow specifying the token address and recipient.


### `I-01` — ERC20 `approve` Function Race Condition  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The standard ERC20 `approve` function is susceptible to a known race condition. If a user approves an amount, and then attempts to change that approval to a different amount before the first transaction is mined, an attacker could front-run the second `approve` transaction. This could result in the spender being able to spend both the original and the new approved amount, effectively doubling the allowance. While `increaseAllowance` and `decreaseAllowance` functions are provided to mitigate this, the base `approve` function still exists.

**Recommendation:** Educate users and integrators to primarily use `increaseAllowance` and `decreaseAllowance` instead of directly calling `approve` when modifying an existing allowance. If `approve` must be used, advise setting the allowance to zero first before setting a new non-zero value.


### `I-02` — Unused `_msgData()` in `Context`  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `_msgData()` function in the `Context` contract contains the statement `this;`. This statement is a no-op and does not affect the contract's logic or state. It can be removed without any functional impact.

**Recommendation:** Remove the `this;` statement from the `_msgData()` function in the `Context` contract for cleaner and more optimized code.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x73d7...d1b4`](https://etherscan.io/address/0x73d7c860998ca3c01ce8c808f5577d94d545d1b4) |
| **Network** | Ethereum |
| **Price** | $0.05282 |
| **24h Volume** | $31.3K |
| **Liquidity** | $516.2K |
| **Volume / Liquidity** | 0.1× |
| **Token Age** | 8mo |
| **Top-10 Holders** | 25.3% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 67 buys / 44 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0xd54a5e98dc3d0a90a058d4e46b2db9e7d92dbf50598833035e1f27eac4f23a4f)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/ixs-token-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-02*
