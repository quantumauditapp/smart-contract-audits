---
token: Ampleforth
ticker: AMPL
network: ethereum
risk_score: 69
status: high
date: 2026-08-31
---

# Ampleforth (AMPL) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 69/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/ampleforth-eth)

---

## Audit Summary

The UFragments (AMPL) contract implements a rebaseable ERC-20 token. It utilizes SafeMath for arithmetic safety and includes EIP-2612 permit functionality. The contract is upgradeable via an AdminUpgradeabilityProxy. A significant finding is the highly centralized control over the token's supply through the `monetaryPolicy` address, which can arbitrarily adjust `_totalSupply` via the `rebase` function. Additionally, unused state variables pose a minor risk for future upgrades.

> **Final Recommendation:** To enhance the security and decentralization of the Ampleforth protocol, it is strongly recommended to implement a multi-signature wallet for the `owner` and `monetaryPolicy` roles. This would distribute control over critical functions like setting the monetary policy and executing rebases, mitigating the risk associated with a single point of failure. Additionally, consider removing unused state variables to streamline the contract and reduce potential storage collision risks during future upgrades.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract demonstrates good technical practices, including the use of SafeMath for robust arithmetic operations and adherence to the ERC-20 standard, along with EIP-712 for permit functionality.… |
| **Governance / Economics** | 1/10 | High | The economic model centers around a rebase mechanism, allowing the `monetaryPolicy` address to adjust the token's total supply. This mechanism is a core design feature of Ampleforth. However, the… |
| **Upgrades** | 1/10 | High | The contract is designed for upgradeability using the `Initializable` pattern and is deployed behind an `AdminUpgradeabilityProxy`. The `ERC20Detailed` base contract includes a `______gap` variable… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Zeppelin Os Legacy |
| **Admin** | Other-Contract |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | 37.0% |
| **Top-3 Unlocked** | 55.1% |

## Security Findings

_🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `H-01` — Centralized Control over Token Supply  *(Severity: High · Status: Unresolved)*

The `owner` address has the ability to set the `monetaryPolicy` address. The `monetaryPolicy` address then has exclusive control over the `rebase` function, which can arbitrarily increase or decrease the token's `_totalSupply`. This grants a single external entity significant power to manipulate the token's supply, posing a high economic risk to token holders. (7.3 Access Control, 7.4 Economic, 7.5 Governance)

**Recommendation:** Consider implementing a multi-signature wallet for the `owner` and `monetaryPolicy` roles to distribute control. Explore a time-locked mechanism or a decentralized governance process for critical supply adjustments to reduce single-point-of-failure risk.


### `M-01` — Unused State Variables and Upgradeability Risk  *(Severity: Medium · Status: Unresolved)*

The contract declares two private state variables, `rebasePausedDeprecated` and `tokenPausedDeprecated`, which are never used in the contract logic. While `private`, these variables still occupy storage slots. In an upgradeable contract using `AdminUpgradeabilityProxy`, changes to storage layout (e.g., removing these variables or changing their order/type in a future implementation) without careful slot management could lead to storage collisions, data corruption, or unexpected behavior in subsequent upgrades. (7.2 Code Security, 7.7 Upgrades)

**Recommendation:** Remove unused state variables to reduce contract complexity and potential for storage collisions during upgrades. If they are intended for future use, ensure their purpose is documented and their storage slots are explicitly managed across upgrades.


### `L-01` — `transferAll` and `transferAllFrom` use `delete`  *(Severity: Low · Status: Unresolved)*

The `transferAll` and `transferAllFrom` functions use `delete _gonBalances[msg.sender]` and `delete _gonBalances[from]` respectively to clear the sender's balance. While functionally correct and gas-efficient for transferring the entire balance, using `delete` explicitly clears the storage slot. This behavior, though not a direct vulnerability, might be unexpected for users accustomed to balances simply becoming zero through subtraction. (7.2 Code Security)

**Recommendation:** Document this behavior clearly for users. Alternatively, consider using `_gonBalances[sender] = 0;` for consistency with typical ERC-20 balance management, although `delete` is more gas-efficient for clearing a non-zero slot.


### `I-01` — `MAX_SUPPLY` Hard Cap  *(Severity: Informational · Status: Unresolved)*

The `_totalSupply` of the token is capped at `type(uint128).max` (approximately 3.4 * 10^38) by the `MAX_SUPPLY` constant. This hard cap is enforced within the `rebase` function. While a very large number, it represents a fixed upper limit on the token's total supply. (7.4 Economic)

**Recommendation:** Ensure that all stakeholders and users are aware of this hard cap and its implications for the token's long-term economic model. This is a design decision rather than a vulnerability, but transparency is key.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xd46b...a161`](https://etherscan.io/address/0xd46ba6d942050d489dbd938a2c909a5d5039a161) |
| **Network** | Ethereum |
| **Price** | $1.2300 |
| **24h Volume** | $949 |
| **Liquidity** | $582.2K |
| **Volume / Liquidity** | 0.0× |
| **Token Age** | 1y |
| **Top-10 Holders** | 496.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 599 buys / 746 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0xc5be99a02c6857f9eac67bbce58df5572498f40c)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/ampleforth-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-31*
