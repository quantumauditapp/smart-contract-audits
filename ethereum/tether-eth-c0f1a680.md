---
token: Tether
ticker: USDT
network: ethereum
risk_score: 12
status: low
date: 2026-10-03
---

# Tether (USDT) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 12/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/tether-eth-c0f1a680)

---

## Audit Summary

The TetherToken contract is an ERC-20 compatible token with significant centralized control. The owner has extensive privileges, including the ability to mint new tokens, burn existing tokens from any address, pause transfers, blacklist individual users, and redirect token logic to a new contract. Additionally, the contract's ERC-20 `transfer`, `transferFrom`, and `approve` functions do not return boolean values as per the standard, which may cause compatibility issues.

> **Final Recommendation:** Token holders should be aware of the extensive centralized control exercised by the contract owner, which includes the ability to mint, burn, freeze, and redirect token functionality. Users should understand the implications of these powers on their holdings and the overall token economy. Integrators should use safe wrappers for ERC-20 interactions due to the non-standard return values of `transfer`, `transferFrom`, and `approve` functions to prevent unexpected behavior.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The TetherToken contract implements a highly centralized architecture where a single owner address holds extensive control over critical token functionalities (7.1 Architecture, 7.3 Access Control).… |
| **Governance / Economics** | 9/10 | Low | The economic model of the TetherToken is entirely controlled by the owner (7.4 Economic, 7.5 Governance). The owner can `issue` new tokens, increasing the total supply and diluting existing holders… |
| **Upgrades** | 10/10 | Low | The contract includes a `deprecate` function (7.7 Upgrades), which allows the owner to redirect all future `transfer` and `transferFrom` calls to an `upgradedAddress`. This mechanism provides a way… |

## Security Findings

_🟢 1 Low · ⚪ 11 Informational_

### `CE-01` — Token transfer functions do not return values as expected by the ERC-20 standard.  *(Severity: Low · Status: Unresolved)*

The `transfer`, `transferFrom`, and `approve` functions in this contract do not return a boolean value, which is required by the ERC-20 standard. While the functions may still work, this non-compliance can cause issues with some wallets, exchanges, or DeFi protocols that expect a return value.

**Recommendation:** Users and integrators should be aware of this non-standard behavior and use safe interaction patterns or wrappers when interacting with these functions to avoid potential compatibility problems.


### `CP-01` — Owner can create new tokens, diluting existing holders.  *(Severity: Informational · Status: Unresolved)*

The contract owner can call the `issue(uint256)` function to create new tokens and add them to the owner's balance. This increases the total supply of tokens, which can dilute the value of tokens held by other users.

**Recommendation:** Token holders should be aware that the supply of tokens is not fixed and can be increased by the owner at any time.


### `CP-02` — Owner can burn tokens from any blacklisted address.  *(Severity: Informational · Status: Unresolved)*

The contract owner can call the `destroyBlackFunds(address)` function, which allows them to remove tokens from any address that has been added to the blacklist. This means the owner can effectively seize and burn tokens belonging to specific users.

**Recommendation:** Token holders should understand that their tokens can be permanently removed from their address if the owner blacklists them and uses this function.


### `CP-03` — Owner can redirect all token transfers to a new contract.  *(Severity: Informational · Status: Unresolved)*

The contract owner can call the `deprecate(address)` function to set a new `upgradedAddress`. Once deprecated, all future `transfer` and `transferFrom` operations will be redirected to this new contract, meaning the owner can unilaterally change the underlying logic and destination of token movements.

**Recommendation:** Token holders should be aware that the owner has the power to migrate the token's functionality to an entirely different contract, which could alter how transfers work or introduce new rules.


### `CP-04` — Owner can stop all token transfers.  *(Severity: Informational · Status: Unresolved)*

The contract owner can call the `pause()` function to temporarily halt all token transfers. While paused, no one, including the owner, can move tokens. The owner can later call `unpause()` to resume transfers.

**Recommendation:** Token holders should know that the owner can prevent them from moving or selling their tokens at any time, which could impact liquidity and access to funds.


### `CP-06` — Owner can prevent specific users from transferring tokens.  *(Severity: Informational · Status: Unresolved)*

The contract owner can use the `addBlackList(address)` function to prevent specific addresses from performing transfers. Conversely, `removeBlackList(address)` can unblock them. This allows the owner to selectively freeze or unfreeze individual user accounts.

**Recommendation:** Token holders should be aware that the owner has the power to block their address, preventing them from moving or selling their tokens.


### `CP-07` — Owner can change fees applied to token transfers.  *(Severity: Informational · Status: Unresolved)*

The contract owner can call the `setParams(uint256,uint256)` function to adjust the `basisPointsRate` (percentage fee) and `maximumFee` applied to token transfers. This means the owner can unilaterally increase or decrease the cost of transacting with the token.

**Recommendation:** Token holders should understand that the fees associated with transferring tokens are subject to change by the owner.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 49.2% of supply. What remains: 43.3% in wallets, 5.9% in other contracts. 15,623,845 holders in total. For a verified reference asset the largest holders are custodians, exchanges and bridges; concentration is reported, not scored.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Tether (USDT), market cap $184.0B, rank #3. On GoPlus's list of trusted tokens. Traded on Binance, Coinbase. 15,623,845 holders. Verified by: CoinGecko, GoPlus, exchange listings.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $75.8M (DexScreener, all pools). 24h trading volume $61.3B (CoinGecko, all markets, daily snapshot). 24h trading volume $68.3M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Stablecoin — issuer-backed (fiat reserves)  *(Severity: Informational · Status: Acknowledged)*

A token designed to hold a fixed value (usually $1). Its safety rests on what backs it and on who can mint, freeze or pause it. Scored as an established reference asset: its identity is verified, so the issuer's or protocol's controls (listed as findings) are real and are priced once as counterparty risk, and LP locks and holder concentration are not scored — its pools belong to market makers and its largest holders are exchanges, bridges and custody. Basis: CoinGecko category: Fiat-backed Stablecoin. Tokenomics — Supply: issued and redeemed by the issuer against its backing. Control: a contract. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $75.8M of DEX liquidity across 30 pools. Launch: 1966 days of market history.

**Recommendation:** Check what backs the peg and who controls supply: reserve attestations for an issuer-backed coin, collateral and governance for a protocol coin.


### `QA-TRADE` — A test sale went through  *(Severity: Informational · Status: Acknowledged)*

We bought 0.01 ETH worth of the token through Uniswap V2 and sold it straight back, inside a simulation of the current block — nothing was signed or sent. Buy tax measured: 0%. Sell tax measured: 0%.

**Recommendation:** This is the state at the time of the audit; an owner who can change taxes or pause trading can change it later.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xdac1...1ec7`](https://etherscan.io/address/0xdac17f958d2ee523a2206206994597c13d831ec7) |
| **Network** | Ethereum |
| **Price** | $0.9992 |
| **24h Volume** | $1.9K |
| **Liquidity** | $1.1K |
| **Volume / Liquidity** | 1.7× |
| **Token Age** | 5y |
| **Top-10 Holders** | 49.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |

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

- [View on DexScreener](https://etherscan.io/address/0xdac17f958d2ee523a2206206994597c13d831ec7)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/tether-eth-c0f1a680)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-03*
