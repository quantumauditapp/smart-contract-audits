---
token: This Is My Iguana
ticker: TIMI
network: base
risk_score: 12
status: low
date: 2026-09-24
---

# This Is My Iguana (TIMI) — Smart Contract Security Analysis | Base

> **Risk Score: 12/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/this-is-my-iguana-base)

---

## Audit Summary

The Erc20 token contract implements standard ERC-20 functionality with an Ownable access control pattern. While leveraging Solidity 0.8.24 for built-in safety and a robust Address library, the contract exhibits critical centralization risks. Specifically, the owner possesses an unrestricted ability to transfer tokens from any address to their own before the token is officially 'launched', bypassing standard ERC-20 approvals. Additionally, the owner has complete control over the token's launch state, which dictates its ability to interact with other smart contracts, and holds the entire initial token supply. These factors introduce significant potential for rug pulls and market manipulation.

> **Final Recommendation:** The project team should immediately address the critical `transferFrom` bypass vulnerability to prevent potential rug pulls or unauthorized token movements by the owner before the token is launched. It is strongly recommended to remove or significantly restrict this functionality. Furthermore, the high degree of centralized control over the token's launch and initial distribution should be clearly communicated to users, and consideration should be given to decentralizing these aspects or implementing a timelock for critical owner actions to enhance trust and reduce single points of failure.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 7/10 | Low | The contract leverages Solidity 0.8.24, providing built-in overflow/underflow protection, and incorporates the robust `Address` library for safe low-level calls (7.2 Code Security). The `Ownable`… |
| **Governance / Economics** | 8/10 | Low | The token's economic model is highly centralized, with the entire initial supply minted to the owner (7.4 Economic). This, combined with a critical `transferFrom` bypass for the owner before the… |
| **Upgrades** | 9/10 | Low | The contract is not designed with upgradeability in mind, meaning its logic is immutable once deployed (7.7 Upgrades). This eliminates upgrade-related risks such as proxy misconfigurations or… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Null Address |

## Security Findings

_🔴 1 Critical · 🟠 1 High · 🟡 1 Medium · 🟢 1 Low_

### `C-01` — Owner's Unrestricted `transferFrom` Before Launch  *(Severity: Critical · Status: Unresolved)*

The `transferFrom` function contains a condition `if (launched == false && to == owner() && msg.sender == owner())` that allows the contract owner to transfer any amount of tokens from any `from` address to their own address (`owner()`) without requiring prior approval (`_allowed`). This bypasses the standard ERC-20 allowance mechanism and grants the owner arbitrary token transfer capabilities before the token is launched, posing a critical centralization risk and potential for a rug pull.

**Recommendation:** Remove the special condition `if (launched == false && to == owner() && msg.sender == owner())` from the `transferFrom` function. All `transferFrom` operations should strictly adhere to the `_allowed` mapping, regardless of the `launched` state or the `msg.sender`.


### `H-01` — Centralized Control Over Token Launch and Contract Interactions  *(Severity: High · Status: Unresolved)*

The `launched` state, controlled solely by the `onlyOwner` function `launch()`, dictates whether the token can interact with other smart contracts (e.g., DEXes, DeFi protocols) via the `_transferAllowed` function. If the owner chooses not to call `launch()`, the token remains unusable in the broader DeFi ecosystem, severely impacting its utility and liquidity. This grants the owner significant power to control the token's market viability and adoption.

**Recommendation:** Consider implementing a decentralized mechanism or a timelock for the `launch()` function to reduce single-point-of-failure risk. Alternatively, clearly document this centralized control and its implications for users and potential integrators.


### `M-01` — Initial Token Distribution Centralization  *(Severity: Medium · Status: Unresolved)*

The entire `totalSupply` is minted to the `owner()` address in the constructor (`_balances[owner()] += _totalSupply;`). While common for new tokens, this high degree of centralization, especially when combined with the owner's ability to bypass `transferFrom` approvals before launch (C-01), means the owner has complete control over the token supply and its initial distribution. This could lead to market manipulation or a rug pull scenario.

**Recommendation:** Implement a more distributed initial token allocation strategy, such as vesting schedules, airdrops, or a public sale, to reduce the concentration of tokens in a single address. If full centralization is intended, ensure this is explicitly communicated to all users.


### `L-01` — Lack of Event Emission for `_transferAllowed` Restrictions  *(Severity: Low · Status: Unresolved)*

The `_transferAllowed` function implements critical logic that restricts transfers to/from contract addresses before the token is launched. However, there's no event emitted when a transfer is blocked due to these restrictions. This lack of visibility makes it harder for users and off-chain systems to understand why a transfer failed, potentially leading to confusion or a poor user experience.

**Recommendation:** Consider emitting a custom event (e.g., `TransferRestricted(address indexed from, address indexed to, uint256 value, string reason)`) within the `_transfer` function when `_transferAllowed` returns `false`. This would provide clearer debugging information and transparency.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x9bee...3777`](https://basescan.org/address/0x9beec80e62aa257ced8b0edd8692f79ee8783777) |
| **Network** | Base |
| **Price** | $0.0001009 |
| **24h Volume** | $45.8K |
| **Liquidity** | $50.0K |
| **Volume / Liquidity** | 0.9× |
| **Token Age** | 2y |
| **Top-10 Holders** | 43.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 226 buys / 229 sells |

## Security Flags (5/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/base/0xa987c7d9109aa93224ba7481f5ca3cae51675556)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/this-is-my-iguana-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-24*
