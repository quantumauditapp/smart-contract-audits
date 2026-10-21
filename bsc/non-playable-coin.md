---
token: Non-Playable Coin
ticker: NPC
network: bsc
risk_score: 36
status: medium
date: 2026-09-05
---

# Non-Playable Coin (NPC) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 36/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/non-playable-coin-bsc)

---

## Audit Summary

The audit covers the TokenImplementation contract, which serves as the logic for a Beacon Proxy-based BridgeToken. The contract implements ERC-20 functionality, including minting, burning, and EIP-2612 permit. Key findings include significant centralized control by the owner over token supply and metadata, inherent front-running risks with the permit function, and the critical need for careful storage layout management during future upgrades. The code generally adheres to good security practices for standard ERC-20 operations.

> **Final Recommendation:** It is recommended to implement robust operational security for the owner address, ideally through a battle-tested multi-signature wallet or a decentralized governance mechanism, given its extensive control over token supply and metadata. For the `permit` function, users should be educated on the risks of front-running and encouraged to use appropriate deadlines. Future upgrades must prioritize rigorous testing of storage layout compatibility to prevent critical issues. Consider replacing the custom `onlyOwner` modifier with OpenZeppelin's `Ownable` for enhanced standardization and audited security features.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract demonstrates good technical security practices, utilizing Solidity 0.8.0+ for automatic integer overflow/underflow protection (7.2 Code Security) and OpenZeppelin libraries for… |
| **Governance / Economics** | 6/10 | Medium | The contract exhibits a high degree of centralized control by the designated `owner` address (7.5 Governance). The owner possesses the ability to `mint` and `burn` tokens, directly influencing the… |
| **Upgrades** | 1/10 | High | The contract is designed as an upgradeable implementation for a Beacon Proxy (7.1 Architecture, 7.7 Upgrades), allowing for future logic updates. The `initialize` function correctly uses an… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Beacon |
| **Implementation** | ✅ Verified source |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 99.9% (≈ permanent lock) |
| **LP Locked** | 99.9% — Null Address |

## Security Findings

_🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `H-01` — Centralized Control over Token Supply and Metadata  *(Severity: High · Status: Unresolved)*

The `owner` address has the ability to `mint` and `burn` tokens, directly affecting the total supply and individual balances. Additionally, the `updateDetails` function allows the owner to change the token's `name` and `symbol`. This level of centralized control introduces significant economic and reputational risk if the owner's private key is compromised or misused. (7.3 Access Control, 7.4 Economic, 7.5 Governance)

**Recommendation:** Implement robust operational security for the owner address, ideally through a battle-tested multi-signature wallet or a decentralized governance mechanism. Clearly communicate the capabilities of the owner to the community and ensure transparency regarding any changes to token metadata or supply.


### `M-01` — Front-Running Risk in Permit Function  *(Severity: Medium · Status: Unresolved)*

The `permit` function, while implementing the EIP-2612 standard, is inherently susceptible to front-running. An attacker could observe a signed `permit` message on the mempool and submit their own transaction with a higher gas price to execute the `permit` before the legitimate user, potentially exploiting the allowance before the intended recipient. This is a known characteristic of the EIP-2612 standard. (7.2 Code Security)

**Recommendation:** Educate users on the risks of front-running with `permit` and advise them to set appropriate `deadline` values. While not a contract-level vulnerability, off-chain strategies or careful transaction submission can mitigate this risk.


### `L-01` — Custom Owner Implementation  *(Severity: Low · Status: Unresolved)*

The contract implements a custom `onlyOwner` modifier and stores the owner address directly in `_state.owner`, rather than inheriting from OpenZeppelin's `Ownable` contract. While functionally similar, using a standard, audited library like OpenZeppelin's `Ownable` is generally preferred for consistency, reduced audit surface, and battle-tested security features (e.g., `transferOwnership`, `renounceOwnership`). (7.2 Code Security)

**Recommendation:** Consider refactoring to inherit from OpenZeppelin's `Ownable` contract to leverage a widely adopted and audited solution, reducing the custom code footprint and potential for subtle bugs.


### `I-01` — Storage Layout Compatibility for Upgrades  *(Severity: Informational · Status: Unresolved)*

The contract utilizes a Beacon Proxy pattern, which allows for upgradeability. Any future upgrades to the `TokenImplementation` logic contract must strictly adhere to the storage layout of the `TokenState` struct and any other state variables declared in the implementation. Deviations in variable order, type, or deletion could lead to storage collisions, data corruption, or unexpected behavior in the proxy, potentially bricking the contract or leading to loss of funds. (7.7 Upgrades)

**Recommendation:** Maintain a strict storage layout for `TokenState` and other state variables across all future implementation versions. Thoroughly test all upgrade scenarios on a testnet, including data migration and function calls, before deploying to production. Consider using tools like OpenZeppelin's `hardhat-upgrades` plugin to assist with storage layout checks.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xfebf...8605`](https://bscscan.com/address/0xfebfa339e44c28e2aa9e62ea1027c9cb4e378605) |
| **Network** | BNB Chain |
| **Price** | $0.02107 |
| **24h Volume** | $242.1K |
| **Liquidity** | $723.0K |
| **Volume / Liquidity** | 0.3× |
| **Token Age** | 1y |
| **Top-10 Holders** | 56.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1159 buys / 1852 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0xb2f3279107da5fde24e6d7337cf4ecaf6c5ada26)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/non-playable-coin-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-05*
