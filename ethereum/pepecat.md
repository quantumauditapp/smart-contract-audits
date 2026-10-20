---
token: PepeCat
ticker: PCAT
network: ethereum
risk_score: 55
status: medium
date: 2026-09-23
---

# PepeCat (PCAT) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 55/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/pepecat-eth)

---

## Audit Summary

The RobinVistaToken contract serves as an ERC20 token implementation for a proxy, utilizing OpenZeppelin's battle-tested ERC20 library. The contract includes a robust initialization mechanism for proxy deployment, preventing re-initialization. However, the design centralizes significant control in the hands of the initializer, who receives the entire initial token supply and becomes the sole entity capable of setting critical pool parameters. While the core ERC20 functionality is secure due to OpenZeppelin's implementation, the centralized control points introduce a notable governance and economic risk.

> **Final Recommendation:** To mitigate the identified risks, it is strongly recommended to decentralize critical control points. Consider implementing a multi-signature wallet or a time-locked contract to manage the `factory` role and the initial token supply. For instance, the `initialize` function could mint tokens to a predefined vault or a governance-controlled address instead of `msg.sender`. Additionally, ensure that all critical setup functions, such as `initialize` and `setPool`, emit events to enhance transparency and off-chain monitoring capabilities. Review the purpose of the `deployer` variable and remove it if it serves no functional purpose to optimize contract size.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract leverages OpenZeppelin's ERC20 implementation, which is a strong foundation for code security (7.2 Code Security), mitigating common vulnerabilities like reentrancy and integer… |
| **Governance / Economics** | 1/10 | High | The economic model and governance structure present a high risk due to significant centralization (7.4 Economic, 7.5 Governance). The `initialize` function allows the `msg.sender` to mint the entire… |
| **Upgrades** | 6/10 | Medium | The contract is designed as an implementation for a proxy, which inherently supports upgradeability (7.7 Upgrades). The `initialize` function includes a robust re-initialization guard (`if (factory… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 83.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟢 2 Low · ⚪ 2 Informational_

### `H-01` — Centralized Control over Initial Supply and Pool Configuration  *(Severity: High · Status: Unresolved)*

The `initialize` function grants `msg.sender` (the address that calls `initialize` on the proxy) the ability to mint the entire `totalSupply_` to themselves. Additionally, this same address is set as the `factory`, which is the only address permitted to call `setPool` to configure critical `poolId` and `baseToken` parameters. This design centralizes significant control in a single entity, creating a single point of failure and potential for misuse or compromise. If the initializer's private key is compromised, the entire token supply and critical pool configurations could be at risk.

**Recommendation:** Implement a more decentralized approach for managing the initial token supply and the `factory` role. Consider the following: 1.  **Initial Supply:** Mint the initial supply to a multi-signature wallet, a timelock contract, or a predefined distribution contract instead of directly to `msg.sender`. 2.  **Factory Role:** Assign the `factory` role to a multi-signature wallet or a governance contract rather than a single EOA. This would require multiple approvals for critical `setPool` operations.…


### `L-01` — Missing Events for Critical Setup Functions  *(Severity: Low · Status: Unresolved)*

The `initialize` and `setPool` functions, which perform critical one-time setup operations for the token and its associated pool, do not emit any events. While state variables are updated, the absence of explicit events makes it harder for off-chain systems (e.g., block explorers, indexers, monitoring tools) to track and verify these crucial configuration changes transparently and efficiently.

**Recommendation:** Emit events for the `initialize` and `setPool` functions to provide clear, auditable records of these critical operations. For example: -   `event Initialized(address indexed initializer, address indexed deployer, uint256 totalSupply);` -   `event PoolSet(bytes32 indexed poolId, address indexed baseToken);` Emitting events enhances transparency, simplifies off-chain monitoring, and improves the overall auditability of the contract's lifecycle.


### `L-02` — Unused `deployer` State Variable  *(Severity: Low · Status: Unresolved)*

The `deployer` state variable is set once during the `initialize` function but is never read or used anywhere else in the contract's logic. While it might be intended for informational purposes, storing an unused variable consumes gas during deployment and state storage, and adds unnecessary complexity to the contract's state.

**Recommendation:** If the `deployer` variable serves no functional purpose within the contract's logic, consider removing it to optimize gas costs and simplify the contract's state. If it is intended purely for informational purposes, consider emitting it in an `Initialized` event instead of storing it as a state variable.


### `I-01` — Constructor Initialization with `address(0xdead)`  *(Severity: Informational · Status: Unresolved)*

The contract's constructor initializes the `factory` variable to `address(0xdead)`. This is a common and effective pattern used in proxy implementation contracts to prevent accidental or malicious direct initialization of the implementation contract itself. Since the proxy's constructor is not called, the `initialize` function's check `if (factory != address(0))` correctly ensures that initialization only occurs once via the proxy.

**Recommendation:** No action required. This is a secure and standard practice for proxy implementations.


### `I-02` — Safe Use of `unchecked` Blocks in ERC20 Standard Library  *(Severity: Informational · Status: Unresolved)*

The OpenZeppelin `ERC20` contract utilizes `unchecked` blocks for arithmetic operations such as `_balances[from] = fromBalance - value;` and `_balances[to] += value;`. These `unchecked` blocks are safely implemented because preceding conditional checks (e.g., `if (fromBalance < value)`) prevent underflow for subtractions, and overflows for additions are generally accepted for token balances given the `uint256` maximum value. This design choice optimizes gas costs without compromising security due to careful preceding logic.

**Recommendation:** No action required. This is a well-audited and secure pattern within the OpenZeppelin library.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x503d...3180`](https://etherscan.io/address/0x503df9169883d258e5c0e6e776f3b017cd2b3180) |
| **Network** | Ethereum |
| **Price** | $0.00005301 |
| **24h Volume** | $202.6K |
| **Liquidity** | $27.7K |
| **Volume / Liquidity** | 7.3× |
| **Token Age** | 19h |
| **Top-10 Holders** | 51.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 631 buys / 438 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x1b6b5dfb107f26fa55478114a566a881b146c16e356bff0b0dcab1f1f4cc2f57)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/pepecat-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-23*
