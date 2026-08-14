---
token: StorjToken
ticker: STORJ
network: ethereum
risk_score: 53
status: high
date: 2026-08-14
---

# StorjToken (STORJ) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 53/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/storjtoken-eth)

---

## Audit Summary

The CentrallyIssuedToken contract implements a standard ERC20 token with burn and migration-based upgrade functionalities. It utilizes SafeMath for arithmetic operations, mitigating common integer overflow/underflow risks. However, the contract exhibits a high degree of centralization through the `upgradeMaster` role, which controls critical upgrade parameters. Several code security patterns, such as the `approve` function's front-running mitigation and the use of `throw` statements, are outdated or introduce usability issues. The upgrade mechanism itself includes important checks for the `UpgradeAgent` but relies heavily on the trustworthiness of the `upgradeMaster`.

> **Final Recommendation:** It is recommended to address the high centralization risk by implementing a multi-signature wallet or a decentralized governance mechanism for the `upgradeMaster` role. This would distribute control and reduce the risk of a single point of failure. Additionally, consider updating the `approve` function to use `increaseAllowance` and `decreaseAllowance` patterns to improve user experience and mitigate front-running risks more effectively. Replace deprecated `throw` and `assert` statements with `require` and `revert` for better gas efficiency and modern Solidity compatibility. Finally, ensure all critical administrative actions, such as changing the `upgradeMaster`, emit corresponding events for transparency and auditability.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The technical architecture (7.1 Architecture) is a multi-inheritance pattern for an ERC20 token with burn and upgrade features. Code security (7.2 Code Security) benefits from SafeMath for… |
| **Governance / Economics** | 1/10 | High | The economic model (7.4 Economic) is a standard centrally issued token with a burn mechanism. The initial supply is minted to a single owner in the constructor. A significant governance risk (7.5… |
| **Upgrades** | 6/10 | Medium | The contract implements a token migration upgrade pattern (7.7 Upgrades), where users actively transfer their tokens to a new `UpgradeAgent` contract. The `setUpgradeAgent` function includes… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 95.2% |
| **Top-3 Unlocked** | ⚠️ 97.6% |

## Security Findings

_🟠 1 High · 🟡 2 Medium · 🟢 1 Low · ⚪ 2 Informational_

### `H-01` — Centralized Control by upgradeMaster  *(Severity: High · Status: Unresolved)*

The `upgradeMaster` address holds significant power, including the ability to set the `upgradeAgent` (which facilitates token migration) and to change the `upgradeMaster` address itself. This single point of control introduces a high centralization risk, as a compromised or malicious `upgradeMaster` could lead to unauthorized token migrations or loss of control over the upgrade process. This impacts 7.3 Access Control and 7.5 Governance.

**Recommendation:** Implement a multi-signature wallet or a decentralized governance mechanism (e.g., a DAO) to control the `upgradeMaster` role. This would require multiple approvals for critical administrative actions, significantly reducing the risk associated with a single point of failure.


### `M-01` — Outdated `approve` Front-Running Mitigation Pattern  *(Severity: Medium · Status: Unresolved)*

The `approve` function includes a check `if ((_value != 0) && (allowed[msg.sender][_spender] != 0)) throw;` which forces users to first set an allowance to zero before increasing it to a new non-zero value. While this pattern attempts to mitigate a specific front-running attack where an attacker can sandwich an `approve` transaction to drain funds, it introduces a cumbersome user experience and does not fully eliminate all front-running scenarios. Modern ERC20 best practices recommend using `increaseAllowance` and `decreaseAllowance` functions. This impacts 7.2 Code Security and 7.4 Economic.

**Recommendation:** Consider replacing the current `approve` logic with `increaseAllowance` and `decreaseAllowance` functions. This provides a safer and more user-friendly way to manage token allowances without requiring a two-step approval process.


### `M-02` — Deprecated `throw` Statements and `assert` Usage  *(Severity: Medium · Status: Unresolved)*

The contract extensively uses `throw` for error handling and `assert` within the `SafeMath` library. In modern Solidity, `require()` and `revert()` are the preferred mechanisms for handling errors related to invalid user input or state, while `assert()` is typically reserved for checking internal invariants. Using `throw` and `assert` for general error conditions can lead to higher gas costs on failure compared to `require`/`revert` in newer EVM versions. This impacts 7.2 Code Security.

**Recommendation:** Refactor the code to replace `throw` statements with `require()` or `revert()` for external input validation and state checks. While `assert` in `SafeMath` is acceptable for invariant checks, consider updating the library to use `revert()` for clarity and consistency if possible.


### `L-01` — Inconsistent `onlyPayloadSize` Modifier Usage  *(Severity: Low · Status: Unresolved)*

The `transfer` function uses the `onlyPayloadSize` modifier, which is an outdated pattern intended to prevent short address attacks. This modifier is generally not effective against modern attacks and can cause unexpected issues. Furthermore, the `transferFrom` function, which also takes address and value arguments, does not use this modifier, leading to inconsistency in the contract's defensive patterns. This impacts 7.2 Code Security.

**Recommendation:** Remove the `onlyPayloadSize` modifier from the `transfer` function. This pattern is largely ineffective and can introduce unnecessary complexity or compatibility issues. Modern Solidity compilers and best practices do not recommend its use.


### `I-01` — Redundant `canUpgrade` Function  *(Severity: Informational · Status: Unresolved)*

The `canUpgrade()` function in `UpgradeableToken` always returns `true`. This makes the `UpgradeState.NotAllowed` branch in `getUpgradeState()` unreachable and renders the `canUpgrade()` function itself redundant. If there are no conditions under which an upgrade should be disallowed, the function serves no practical purpose. This impacts 7.1 Architecture.

**Recommendation:** Either remove the `canUpgrade()` function if it's not intended to ever return `false`, or implement actual conditions within it that determine whether an upgrade is allowed. If removed, adjust `getUpgradeState()` accordingly.


### `I-02` — Missing Event for `setUpgradeMaster`  *(Severity: Informational · Status: Unresolved)*

The `setUpgradeMaster` function allows the current `upgradeMaster` to transfer its administrative role to a new address. This is a critical administrative action, but no event is emitted to log this change on-chain. The absence of an event makes it difficult to track changes in the `upgradeMaster` role, hindering transparency and auditability of administrative actions. This impacts 7.2 Code Security and 7.8 Operations.

**Recommendation:** Emit an event (e.g., `UpgradeMasterChanged(address indexed oldMaster, address indexed newMaster)`) whenever the `upgradeMaster` address is updated. This provides an on-chain record of the change, improving transparency and making administrative actions easier to monitor and audit.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xb64e...b8ac`](https://etherscan.io/address/0xb64ef51c888972c908cfacf59b47c1afbc0ab8ac) |
| **Network** | Ethereum |
| **Price** | $0.0443 |
| **24h Volume** | $38.6K |
| **Liquidity** | $79.3K |
| **Volume / Liquidity** | 0.5× |
| **Token Age** | 6y |
| **Top-10 Holders** | 61.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 300 buys / 272 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0xaef16913b6c50ebcf627a394921f306985fc8604)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/storjtoken-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-14*
