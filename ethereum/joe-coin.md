---
token: Joe Coin
ticker: JOE
network: ethereum
risk_score: 0
status: low
date: 2026-09-04
---

# Joe Coin (JOE) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 0/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/joe-coin-eth)

---

## Audit Summary

The Joe Token contract is an ERC20 token with custom fee mechanisms and automated liquidity features. The audit identified a high-severity issue related to unchecked arithmetic in balance updates within the ERC20 base contract. Other findings include high immutable transaction fees, lack of emergency pause functionality, and informational risks concerning automated swaps and hardcoded addresses. A significant positive is the renounced ownership, which effectively removes many centralization risks associated with owner privileges.

> **Final Recommendation:** It is strongly recommended to review and address the unchecked arithmetic in the `_update` and `_transfer` functions to ensure robust overflow protection for all balance modifications. While `uint256` overflows are rare in practice for typical token supplies, explicit checks or removal of `unchecked` blocks for additions are crucial for maintaining the highest security standards. Additionally, consider the long-term implications of the high, immutable transaction fees on user adoption and trading volume.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 9/10 | Low | The contract implements a standard ERC20 token with custom transfer logic, including various fees and anti-whale mechanisms. A high-severity vulnerability was identified where critical balance… |
| **Governance / Economics** | 10/10 | Low | The tokenomics include a significant total transaction fee (up to 25%) which is immutable due to renounced ownership (7.4 Economic). While this prevents malicious changes, it fixes a potentially high… |
| **Upgrades** | 10/10 | Low | The contract is not designed with an upgrade mechanism (e.g., proxy pattern), meaning its logic is immutable once deployed (7.7 Upgrades). This eliminates upgrade-related risks such as proxy… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Locked** | 100.0% — Null Address, UNCX |
| **Lock Expiry** | ✅ 2280 (verified ≥ 1 year) — UNCX V2 |

## Security Findings

_🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 2 Informational_

### `H-01` — Unchecked Arithmetic in ERC20 Base and Joe Token  *(Severity: High · Status: Unresolved)*

The `ERC20` base contract's `_update` function, which is responsible for modifying token balances and total supply, explicitly uses `unchecked` blocks for addition operations (`_balances[to] = _balances[to] + amount;` and `_totalSupply = _totalSupply + amount;`). Similarly, the `Joe` token's overridden `_transfer` function may also contain `unchecked` blocks for balance updates. While Solidity 0.8.x generally provides default overflow/underflow protection, `unchecked` blocks disable these checks. This could theoretically lead to an integer overflow if `_balances[to]` or `_totalSupply` were to exceed `type(uint256).max` after an addition, resulting in incorrect token balances or total supply.

**Recommendation:** Remove the `unchecked` blocks around addition operations in the `_update` function and any direct balance manipulations in the `_transfer` function. Rely on Solidity 0.8.x's default overflow protection. If `unchecked` is intentionally used for gas optimization, ensure that mathematical invariants are rigorously proven to prevent overflow conditions under all circumstances.


### `M-01` — High and Immutable Transaction Fees  *(Severity: Medium · Status: Unresolved)*

The contract implements a total transaction fee of up to 25% (5% tax, 5% liquidity, 5% burn, 10% marketing). While the ownership has been renounced, making these fee percentages immutable, such a high fixed fee can significantly impact token usability, trading volume, and user perception. It can lead to high price impact on trades, deter legitimate transactions, and potentially reduce the token's overall market appeal and liquidity over time.

**Recommendation:** While the fees are immutable due to renounced ownership, it is important for the project to clearly communicate these high fees to potential users and investors. Future token designs should carefully consider the long-term economic impact of such high transaction taxes on user adoption and ecosystem growth.


### `L-01` — Lack of Emergency Pause Functionality  *(Severity: Low · Status: Unresolved)*

The contract lacks a mechanism to pause transfers or other critical functions in case of an emergency, such as a discovered critical bug, exploit, or market manipulation event. While ownership is renounced, preventing a centralized entity from pausing, the absence of any decentralized or community-governed pause mechanism leaves the protocol vulnerable to unmitigated risks in unforeseen circumstances.

**Recommendation:** Consider implementing a decentralized pause mechanism, possibly through a multi-signature wallet or a community governance system, for future contracts. For this deployed contract, acknowledge that no emergency pause is possible and ensure all other security measures are robust.


### `I-01` — Potential for Sandwich Attacks on Automated Swaps  *(Severity: Informational · Status: Unresolved)*

The `swapAndLiquify` function performs automated swaps via Uniswap to manage liquidity. If the `swapTokensAtAmount` threshold for triggering these swaps is predictable or can be monitored, malicious actors could potentially front-run or sandwich these transactions. This involves placing a transaction before and after the automated swap to profit from the price impact, potentially increasing slippage for the protocol's liquidity addition and reducing its efficiency.

**Recommendation:** While difficult to fully prevent in public mempools, consider strategies to randomize or obscure the timing of automated swaps in future designs. For the current contract, acknowledge this inherent risk associated with automated liquidity mechanisms interacting with AMMs.


### `I-02` — Hardcoded Uniswap V2 Router Address  *(Severity: Informational · Status: Unresolved)*

The Uniswap V2 Router address is hardcoded in the contract's constructor. While this is a common practice and router addresses are generally stable, if the router address were to change or become compromised in the future, the contract's automated liquidity and swap functionalities would cease to work. This would require a new contract deployment to update the address.

**Recommendation:** For future contracts, consider making critical external contract addresses configurable by a trusted entity (e.g., a multi-sig wallet) or through a governance mechanism, even if ownership is later renounced. For the current contract, this is a known limitation.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x76e2...49a8`](https://etherscan.io/address/0x76e222b07c53d28b89b0bac18602810fc22b49a8) |
| **Network** | Ethereum |
| **Price** | $0.006024 |
| **24h Volume** | $235.9K |
| **Liquidity** | $1.34M |
| **Volume / Liquidity** | 0.2× |
| **Token Age** | 2y |
| **Top-10 Holders** | 24.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 102 buys / 54 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x704ad8d95c12d7fea531738faa94402725acb035)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/joe-coin-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-04*
