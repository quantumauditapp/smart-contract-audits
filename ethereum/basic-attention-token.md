---
token: Basic Attention Token
ticker: BAT
network: ethereum
risk_score: 34
status: low
date: 2026-10-11
---

# Basic Attention Token (BAT) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 34/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/basic-attention-token-eth)

---

## Audit Summary

The BAToken contract implements an ERC-20-like token with integrated crowdsale functionality. While `SafeMath` is used for critical crowdsale calculations, the inherited `StandardToken` contract contains an integer overflow vulnerability in its addition operations. The contract also utilizes an outdated Solidity compiler version and older patterns like `send()` with fixed gas limits, which introduce additional risks. The design is non-upgradeable, making any discovered vulnerability permanent.

> **Final Recommendation:** It is strongly recommended to refactor the `StandardToken` contract to incorporate `SafeMath` for all arithmetic operations, especially additions, to prevent integer overflows. Additionally, update the Solidity compiler version to a recent stable release (e.g., 0.8.x) and replace `throw` statements with `require()` or `revert()` for improved gas efficiency and clearer error handling. For external ETH transfers, consider using `.call{value: ...}('')` with appropriate reentrancy guards instead of `.send()` to avoid fixed gas limit issues. Implement a two-step approval mechanism for the ERC-20 `approve` function to mitigate the known race condition.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract demonstrates a basic architecture for an ERC-20 token with crowdsale features (7.1 Architecture). Strengths include the use of `SafeMath` for crowdsale-specific arithmetic and clear… |
| **Governance / Economics** | 4/10 | Medium | The economic model for the crowdsale is clearly defined with `fundingStartBlock`, `fundingEndBlock`, `tokenCreationCap`, and `tokenCreationMin` (7.4 Economic). Refund conditions are appropriately set… |
| **Upgrades** | 3/10 | High | The contract is not designed with any upgradeability mechanism (7.7 Upgrades). This means that once deployed, its logic is immutable. While this offers simplicity and reduces the complexity… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | 31.8% |
| **Top-3 Unlocked** | 59.6% |

## Security Findings

_🟡 5 Medium · 🟢 1 Low · ⚪ 5 Informational_

### `M-01` — ERC-20 `approve` Race Condition Vulnerability  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `approve` function in `StandardToken` is susceptible to a known ERC-20 race condition. If a user approves an amount for a spender, and then approves a *different* (typically lower) amount before the spender has spent the original allowance, the spender might be able to spend both the original and the new allowance. This occurs because the spender can execute a `transferFrom` transaction with the original allowance after the new approval transaction is mined but before the original allowance is updated, effectively allowing them to spend more than intended.

**Recommendation:** To mitigate this, implement a two-step approval process (e.g., `increaseAllowance` and `decreaseAllowance` functions) or the 'approve and call' pattern. This prevents the spender from exploiting the race condition by requiring them to first set the allowance to zero before setting a new value.


### `M-02` — Fixed Gas Limit for External ETH Transfers (`.send()`)  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `finalize()` and `refund()` functions use the `.send()` method for transferring ETH to external addresses (`ethFundDeposit` and `msg.sender`, respectively). The `.send()` function has a fixed gas stipend of 2300. This amount is often insufficient for recipient contracts that have complex fallback functions or require more gas to process the incoming ETH. If the recipient contract's fallback function consumes more than 2300 gas, the ETH transfer will fail, potentially locking funds in the contract or preventing the successful finalization of the crowdsale or user refunds.

**Recommendation:** Consider using `.call{value: ethVal}('')` for external ETH transfers, as it forwards all available gas by default. When using `.call`, it is crucial to implement robust reentrancy guards (e.g., OpenZeppelin's `ReentrancyGuard`) to prevent reentrancy attacks, although in this specific contract, state changes occur before the `send` call, mitigating direct reentrancy for the same transaction.


### `M-03` — Integer Overflow in StandardToken `transfer` and `transferFrom`  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `StandardToken` contract, inherited by `BAToken`, does not utilize `SafeMath` for addition operations within its `transfer` and `transferFrom` functions. Specifically, the line `balances[_to] += _value;` in both functions is vulnerable to integer overflow. If `balances[_to]` is sufficiently large and `_value` is also large, their sum could exceed `uint256`'s maximum value, causing the balance to wrap around to a small number. This could lead to an incorrect balance for the recipient, potentially allowing them to receive fewer tokens than intended or disrupting the total supply accounting.

**Recommendation:** Implement `SafeMath` for all arithmetic operations in `StandardToken`. Specifically, replace `balances[_to] += _value;` with `balances[_to] = safeAdd(balances[_to], _value);` in both `transfer` and `transferFrom` functions.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 85.0% is held, unlocked, by 10 address(es) other than the owner/deployer. No single one holds a majority: their exits thin the market rather than hand anyone the pool. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them. This assessment covers the main pool, which holds 60% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-POWERS` — What the token's controller can do  *(Severity: Medium · Status: Acknowledged)*

The contract lets its controller — an owner that could not be resolved — mint new supply. Nothing independent vouches for whoever holds them, so each is a live risk to holders.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `L-01` — Use of Outdated Solidity Version and `throw` Statement  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract is compiled with Solidity `^0.4.10`, which is an outdated version. This version lacks many security features, optimizations, and best practices introduced in later Solidity releases. Additionally, the contract uses `throw` statements for error handling. `throw` consumes all remaining gas upon failure, which is less gas-efficient than `revert()` or `require()` (introduced in Solidity 0.4.10 and 0.4.22 respectively), which refund unused gas.

**Recommendation:** Upgrade the Solidity compiler version to a more recent stable release (e.g., `^0.8.0`). This will enable automatic overflow/underflow checks and provide access to modern language features. Refactor all `throw` statements to `require()` or `revert()` for improved gas efficiency and clearer error messages.


### `I-01` — Lack of Emergency Pause/Withdrawal Mechanism  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract lacks a mechanism to pause critical operations (such as token transfers or crowdsale participation) or to perform emergency withdrawals of funds in case of unforeseen vulnerabilities or critical issues. While the crowdsale has specific `finalize` and `refund` conditions, there is no general 'kill switch' or pause functionality that could be activated by an authorized entity (e.g., a multi-signature wallet) to mitigate risks from unknown vulnerabilities or external attacks.

**Recommendation:** For future contracts, consider implementing a well-designed pause mechanism (e.g., using OpenZeppelin's `Pausable` contract) and/or an emergency withdrawal function, typically controlled by a multi-signature wallet, to provide a safety net in critical situations.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 39.9% of supply. What remains: 37.9% in wallets, 2.0% in other contracts. 421,236 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Basic Attention (BAT), market cap $204M, rank #188. On GoPlus's list of trusted tokens. Traded on Binance, Coinbase. 421,236 holders. Verified by: CoinGecko, GoPlus, exchange listings.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $495K (DexScreener, all pools). 24h trading volume $87.3M (CoinGecko, all markets, daily snapshot). 24h trading volume $388K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $1.90 on 2021-11-27; the price is now 92.8137% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $495K of DEX liquidity across 24 pools. Launch: 2336 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x0d87...87ef`](https://etherscan.io/address/0x0d8775f648430679a709e98d2b0cb6250d2887ef) |
| **Network** | Ethereum |
| **Price** | $0.142 |
| **24h Volume** | $30.8K |
| **Liquidity** | $297.7K |
| **Volume / Liquidity** | 0.1× |
| **Token Age** | 6y |
| **Top-10 Holders** | 39.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 369 buys / 404 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0xae614a7a56cb79c04df2aeba6f5dab80a39ca78e)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/basic-attention-token-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-11*
