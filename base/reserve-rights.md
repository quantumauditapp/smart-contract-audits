---
token: Reserve Rights
ticker: RSR
network: base
risk_score: 58
status: medium
date: 2026-10-12
---

# Reserve Rights (RSR) — Smart Contract Security Analysis | Base

> **Risk Score: 58/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/reserve-rights-base)

---

## Audit Summary

This report details the security audit of the OptimismMintableERC20 token contract. The contract functions as a standard ERC-20 token with an additional minting capability. A key finding is that a privileged bridge address can mint new tokens, which could dilute existing token holders.

> **Final Recommendation:** Token holders should be aware of the centralized minting capability controlled by the designated bridge address. It is crucial to understand the operational security and governance of this bridge, as its compromise could lead to uncontrolled token inflation. Regular monitoring of the bridge's activity and any associated governance decisions is recommended to assess potential impacts on token supply and value.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The OptimismMintableERC20 contract correctly implements the standard ERC-20 token interface, providing essential functionalities like `transfer`, `balanceOf`, and `approve`. Its architecture is… |
| **Governance / Economics** | 1/10 | High | The contract's economic model is clear, with minting explicitly tied to a bridge mechanism, which can be beneficial for cross-chain liquidity. The `mint` function, callable only by the `bridge`… |
| **Upgrades** | 3/10 | High | The OptimismMintableERC20 contract is not implemented as an upgradeable proxy (7.7 Upgrades). This design choice provides immutability, meaning its logic cannot be altered after deployment, which… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 81.3% |
| **Top-3 Unlocked** | ⚠️ 95.9% |

## Security Findings

_🟡 2 Medium · ⚪ 4 Informational_

### `CP-01` — Privileged Address Can Mint New Tokens  *(Severity: Medium · Status: Unresolved)*

The `mint(address _to, uint256 _amount)` function allows a specific, privileged address, referred to as the 'bridge,' to create new tokens and add them to the total supply. This means the total number of tokens can be increased at any time by the bridge controller. If the bridge's private key is compromised or if the bridge operator acts maliciously, they could mint an arbitrary amount of tokens, which would dilute the value of all existing tokens held by other users.

**Recommendation:** Token holders should understand that the value of their tokens is subject to the minting policy controlled by the bridge. It is important to research and trust the entity or mechanism that controls the 'bridge' address. Ensure there are robust security measures and transparent operational procedures in place for the bridge to prevent unauthorized or excessive minting.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 6 address(es) other than the owner/deployer. One of them — a wallet, 0xa9e0…46c1 — holds 81.3% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them. This assessment covers the main pool, which holds 55% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 77.0% of supply. What remains: 70.5% in wallets, 6.5% in other contracts. 84,593 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Reserve Rights (RSR), market cap $104M, rank #288. Traded on Binance, Coinbase. 84,593 holders. Verified by: CoinGecko, exchange listings.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $143K (DexScreener, all pools). 24h trading volume $4.4M (CoinGecko, all markets, daily snapshot). 24h trading volume $388K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $0.117 on 2021-04-16; the price is now 98.5837% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: bridge — a contract. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $143K of DEX liquidity across 19 pools. Launch: 1030 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xab36...f64a`](https://basescan.org/address/0xab36452dbac151be02b16ca17d8919826072f64a) |
| **Network** | Base |
| **Price** | $0.00238 |
| **24h Volume** | $269.3K |
| **Liquidity** | $78.9K |
| **Volume / Liquidity** | 3.4× |
| **Token Age** | 2y |
| **Top-10 Holders** | 77.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 484 buys / 438 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0x11e26bbd1a5547895a50fc39a2d4c0025dec0bda)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/reserve-rights-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-12*
