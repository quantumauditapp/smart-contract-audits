---
token: SuperVerse
ticker: SUPER
network: ethereum
risk_score: 61
status: high
date: 2026-07-31
---

# SuperVerse (SUPER) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 61/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/superverse-eth)

---

## Audit Summary

The SuperFarm Token contract implements a standard ERC-20 token with a fixed supply cap and Compound-style voting delegation. It leverages OpenZeppelin contracts for core ERC-20 and access control functionalities. The audit identified a high-severity centralization risk related to token minting and a medium-severity concern regarding front-running in signature-based delegation. Several low-severity and informational findings were also noted, primarily concerning operational flexibility and compiler version.

> **Final Recommendation:** It is recommended to address the centralized minting authority by implementing a multi-signature wallet or a time-locked mechanism for minting operations to enhance decentralization and transparency. While the `delegateBySig` front-running is a known blockchain characteristic, users should be informed of this potential risk. For future iterations, consider upgrading to a newer Solidity compiler version to benefit from improved security features and implementing an emergency pause mechanism for operational resilience.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 7/10 | Low | The contract is built upon battle-tested OpenZeppelin libraries (ERC20Capped, Ownable), which enhances its foundational security (7.2 Code Security). The voting mechanism is a well-understood pattern… |
| **Governance / Economics** | 2/10 | High | The token features a fixed supply cap, preventing inflationary attacks beyond the initial design (7.4 Economic). The voting delegation mechanism is standard, promoting decentralized governance… |
| **Upgrades** | 3/10 | High | The contract is not designed to be upgradeable. This simplifies the architecture by removing the complexities and risks associated with proxy patterns (7.7 Upgrades). However, it means that any… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 72.0% |
| **Top-3 Unlocked** | ⚠️ 87.7% |

## Security Findings

_🟠 1 High · 🟡 1 Medium · 🟢 2 Low_

### `H-01` — Centralized Minting Authority  *(Severity: High · Status: Unresolved)*

The `mint` function is restricted to the contract owner, allowing them to mint tokens up to the predefined cap. This grants significant control over the token supply and distribution, which could influence governance outcomes if the owner mints tokens to themselves or allied addresses without proper oversight. (7.3 Access Control, 7.4 Economic)

**Recommendation:** Consider implementing a multi-signature wallet for ownership of the `mint` function or a time-locked mechanism for minting operations. This would decentralize control and increase transparency, reducing the risk of a single point of failure or malicious action.


### `M-01` — `delegateBySig` Expiry Front-running  *(Severity: Medium · Status: Unresolved)*

The `delegateBySig` function uses `now <= expiry` to check signature validity. This check is susceptible to miner front-running, where a malicious miner could manipulate transaction inclusion order to cause a valid signature to expire or an expired signature to be included, within the same block. (7.2 Code Security, 7.6 External)

**Recommendation:** While this is a common pattern and a general characteristic of blockchain transactions, users should be aware of this potential front-running risk for time-sensitive delegation. For critical operations, consider alternative mechanisms or ensure users understand the implications.


### `L-01` — Older Solidity Compiler Version  *(Severity: Low · Status: Unresolved)*

The contract uses Solidity 0.6.12. While functional and compatible with OpenZeppelin 3.x, newer versions (e.g., 0.8.x) include built-in overflow/underflow checks by default, reducing reliance on SafeMath libraries and potentially simplifying code while enhancing security. (7.2 Code Security)

**Recommendation:** Consider upgrading to a more recent Solidity compiler version (e.g., 0.8.x) for future deployments or significant updates to benefit from improved security features, optimizations, and reduced bytecode size. Ensure thorough testing if upgrading.


### `L-02` — Lack of Emergency Pause Mechanism  *(Severity: Low · Status: Unresolved)*

The contract lacks a mechanism to pause critical operations (e.g., transfers, minting) in case of an emergency, such as a discovered vulnerability in the token itself or a major external exploit impacting the ecosystem. This limits the ability to react swiftly to unforeseen events. (7.8 Operations)

**Recommendation:** For future iterations, consider implementing a `Pausable` mechanism (e.g., from OpenZeppelin) controlled by a multi-signature wallet or governance. This would provide an emergency stop-gap to mitigate damage in critical situations.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xe53e...0a55`](https://etherscan.io/address/0xe53ec727dbdeb9e2d5456c3be40cff031ab40a55) |
| **Network** | Ethereum |
| **Price** | $0.08275 |
| **24h Volume** | $60.0K |
| **Liquidity** | $1.97M |
| **Volume / Liquidity** | 0.0× |
| **Token Age** | 5y |
| **Top-10 Holders** | 58.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 74 buys / 88 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0x25647e01bd0967c1b9599fa3521939871d1d0888)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/superverse-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-07-31*
