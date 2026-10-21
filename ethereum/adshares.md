---
token: Adshares
ticker: ADS
network: ethereum
risk_score: 49
status: medium
date: 2026-09-12
---

# Adshares (ADS) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 49/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/adshares-eth)

---

## Audit Summary

The audit of the WrappedADS ERC20 token contract identified a high-severity centralization risk related to the Pauser role, which could lead to a single point of failure and potential permanent loss of control over the pausing mechanism. Minor issues include an outdated Solidity compiler version and a negligible gas optimization opportunity. The contract otherwise follows standard ERC20 implementations with robust arithmetic safety.

> **Final Recommendation:** It is strongly recommended to address the centralization risk associated with the `PauserRole`. Consider implementing a multi-signature wallet for the pauser role or a more decentralized governance mechanism to mitigate the single point of failure and prevent accidental permanent loss of control. Additionally, upgrading the Solidity compiler version to a more recent stable release is advised to benefit from the latest security features and optimizations.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 7/10 | Low | The contract implements a standard ERC20 token with pausing capabilities, leveraging OpenZeppelin-like patterns and `SafeMath` for arithmetic safety (7.2 Code Security). The architecture is clear… |
| **Governance / Economics** | 1/10 | High | The token's economic model is a standard ERC20, with no complex DeFi primitives or oracle dependencies (7.4 Economic). There are no explicit governance mechanisms beyond the `PauserRole` (7.5… |
| **Upgrades** | 3/10 | High | The contract is not designed to be upgradeable, as indicated by `is_proxy: false` (7.7 Upgrades). This eliminates upgrade-related risks such as proxy storage collisions or logic errors during… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟢 1 Low · ⚪ 1 Informational_

### `H-01` — Centralized Pauser Role with Potential for Permanent Loss of Control  *(Severity: High · Status: Unresolved)*

The `PauserRole` grants significant control to a single `Pauser` address (initially the deployer) to pause and unpause all token transfers. This introduces a high centralization risk. Furthermore, the `renouncePauser()` function allows any pauser to remove themselves from the role. If the *sole* pauser renounces their role without first assigning a new pauser, the contract will be left without any active pausers. In this scenario, no new pausers can be added, and the pausing mechanism (both `pause()` and `unpause()`) would become permanently inaccessible, potentially locking the contract in a paused or unpaused state indefinitely.

**Recommendation:** Implement a more robust and decentralized access control mechanism for the pauser role. Consider using a multi-signature wallet (e.g., Gnosis Safe) for the `Pauser` address. Alternatively, modify the `renouncePauser` function to prevent the sole pauser from renouncing their role unless a new pauser has already been designated, or implement a timelock for critical role changes.


### `L-01` — Outdated Solidity Compiler Version  *(Severity: Low · Status: Unresolved)*

The contract uses Solidity `^0.5.0`. While `SafeMath` is used to mitigate common arithmetic overflows, newer compiler versions (e.g., `^0.8.0`) offer built-in overflow checks, improved security features, and gas optimizations. Using an older version might expose the contract to known compiler bugs or make it harder to integrate with newer tools and libraries.

**Recommendation:** Consider upgrading the Solidity compiler version to a more recent stable release (e.g., `^0.8.0` or higher). This would allow for the removal of `SafeMath` (as `uint256` operations would revert on overflow/underflow by default) and provide access to the latest language features and security improvements. Thorough testing would be required after such an upgrade.


### `I-01` — Unnecessary `this;` in `_msgData()`  *(Severity: Informational · Status: Unresolved)*

The `_msgData()` function in the `Context` contract includes an unnecessary `this;` statement. This statement has no functional effect and can be removed.

**Recommendation:** Remove the `this;` statement from the `_msgData()` function to slightly reduce bytecode size and improve readability, although the gas impact is negligible.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xcfce...d22a`](https://etherscan.io/address/0xcfcecfe2bd2fed07a9145222e8a7ad9cf1ccd22a) |
| **Network** | Ethereum |
| **Price** | $0.4668 |
| **24h Volume** | $240.3K |
| **Liquidity** | $941.0K |
| **Volume / Liquidity** | 0.3× |
| **Token Age** | 1y |
| **Top-10 Holders** | 98.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 273 buys / 256 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0x16a92c8f5fc3087690bc09389fa7e038c47fa26b4f0ca978509d366a62982185)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/adshares-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-12*
