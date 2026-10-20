---
token: Decentraland
ticker: MANA
network: ethereum
risk_score: 35
status: medium
date: 2026-10-03
---

# Decentraland (MANA) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 35/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/decentraland-eth)

---

## Audit Summary

The MANAToken contract is an ERC-20 token with standard functionalities including minting, burning, and pausing. It utilizes the Ownable pattern for administrative control and SafeMath for arithmetic operations. The primary risks stem from the significant centralized control held by the owner, which is typical for tokens of this era. The contract is not upgradeable, simplifying its architecture.

> **Final Recommendation:** It is recommended to implement a multi-signature wallet for the `owner` address to mitigate the high centralization risk associated with minting and pausing capabilities. Consider emitting an event when ownership is transferred to enhance transparency and off-chain monitoring. For any future token deployments, consider using a more recent Solidity compiler version and audited libraries to benefit from modern security features and best practices.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract employs the SafeMath library to prevent integer overflow/underflow vulnerabilities, a strong practice for Solidity 0.4.x. Standard ERC-20 functions are implemented correctly, and the… |
| **Governance / Economics** | 4/10 | Medium | The contract design grants significant centralized control to the `owner` address (7.3 Access Control). The owner can mint an unlimited supply of new tokens, effectively inflating the total supply… |
| **Upgrades** | 4/10 | Medium | The MANAToken contract is not designed as an upgradeable proxy (7.7 Upgrades). This eliminates upgrade-related risks such as proxy implementation mismatches or storage collisions. The `Ownable`… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | 43.0% |
| **Top-3 Unlocked** | 79.3% |

## Security Findings

_🟠 2 High · 🟡 2 Medium · 🟢 1 Low · ⚪ 6 Informational_

### `H-01` — Centralized Control by Owner  *(Severity: High · Status: Unresolved)*

The `owner` address has extensive control over the token's core functionalities. This includes the ability to `mint` an unlimited number of new tokens, which can dilute the value of existing tokens, and the ability to `pause` all token transfers, effectively freezing the token (7.3 Access Control, 7.4 Economic). This presents a single point of failure and a high centralization risk.

**Recommendation:** Implement a multi-signature wallet (e.g., Gnosis Safe) for the `owner` address to distribute control and require multiple approvals for critical operations like minting or pausing. This significantly reduces the risk of a single point of failure or malicious action.


### `QA-POWERS` — What the token's controller can do  *(Severity: High · Status: Acknowledged)*

The contract lets its controller — a ProxyAdmin contract — mint new supply; pause all transfers. Nothing independent vouches for whoever holds them, so each is a live risk to holders.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `M-01` — Missing Event for Ownership Transfer  *(Severity: Medium · Status: Unresolved)*

The `transferOwnership` function in the `Ownable` contract allows the owner to transfer administrative control to a new address, but it does not emit an event to signal this critical change (7.5 Governance). This makes it difficult for off-chain systems, users, or monitoring tools to track ownership changes reliably.

**Recommendation:** Add an `event OwnershipTransferred(address indexed previousOwner, address indexed newOwner);` and emit it within the `transferOwnership` function after the `owner` is updated.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 90.6% is held, unlocked, by 10 address(es) other than the owner/deployer. No single one holds a majority: their exits thin the market rather than hand anyone the pool. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them. This assessment covers the main pool, which holds 53% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `L-01` — SafeMath.div Does Not Explicitly Check for Division by Zero  *(Severity: Low · Status: Unresolved)*

The `div` function in the `SafeMath` library, as implemented, does not explicitly check if the divisor `b` is zero before performing the division (7.2 Code Security). While Solidity's default behavior would revert on division by zero, an explicit `require(b > 0)` check would make the intent clearer and provide a more informative error message. In this specific contract, `div` is not used in a critical path with user-controlled input.

**Recommendation:** For robustness, consider adding `require(b > 0, "SafeMath: division by zero");` at the beginning of the `div` function in `SafeMath`.


### `I-01` — Outdated Solidity Compiler Version  *(Severity: Informational · Status: Unresolved)*

The contract is compiled with Solidity version `^0.4.11`. This version is significantly outdated and lacks many security features, optimizations, and bug fixes present in newer compiler versions (e.g., 0.6.x, 0.8.x) (7.2 Code Security). While the code itself might be robust for its era, newer versions offer improved safety and better error handling.

**Recommendation:** For any new deployments or significant upgrades, consider migrating to a recent, stable Solidity compiler version (e.g., 0.8.x) to leverage modern security enhancements and best practices.


### `I-02` — ERC-20 Approve Race Condition Mitigation Trade-off  *(Severity: Informational · Status: Unresolved)*

The `approve` function includes a check `require((_value == 0) \|\| (allowed[msg.sender][_spender] == 0));` to mitigate the known ERC-20 `approve` race condition (7.2 Code Security). While this prevents a specific front-running scenario, it also restricts legitimate use cases where a user might want to increase an existing allowance without first setting it to zero, requiring two transactions instead of one.

**Recommendation:** Acknowledge this design choice. For future token designs, consider using `increaseAllowance` and `decreaseAllowance` functions (as introduced in OpenZeppelin's ERC-20 implementations) which provide a safer way to modify allowances without the need for a zero-value transaction.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 45.3% of supply. What remains: 33.8% in wallets, 11.5% in other contracts. 277,568 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Decentraland (MANA), market cap $209M, rank #190. Traded on Binance, Coinbase. 277,568 holders. Verified by: CoinGecko, exchange listings.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $173K (DexScreener, all pools). 24h trading volume $175.4M (CoinGecko, all markets, daily snapshot). 24h trading volume $126K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $5.85 on 2021-11-25; the price is now 98.1779% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: a ProxyAdmin contract. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $173K of DEX liquidity across 18 pools. Launch: 2328 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x0f5d...c942`](https://etherscan.io/address/0x0f5d2fb29fb7d3cfee444a200298f468908cc942) |
| **Network** | Ethereum |
| **Price** | $0.1023 |
| **24h Volume** | $81.2K |
| **Liquidity** | $92.3K |
| **Volume / Liquidity** | 0.9× |
| **Token Age** | 6y |
| **Top-10 Holders** | 45.3% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 577 buys / 561 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x11b1f53204d03e5529f09eb3091939e4fd8c9cf3)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/decentraland-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-03*
