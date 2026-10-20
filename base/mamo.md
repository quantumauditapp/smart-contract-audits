---
token: Mamo
ticker: MAMO
network: base
risk_score: 42
status: medium
date: 2026-10-05
---

# Mamo (MAMO) — Smart Contract Security Analysis | Base

> **Risk Score: 42/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/mamo-base)

---

## Audit Summary

The MAMO contract is an ERC-20 token with standard functionalities including burning, voting, and permit features. The contract incorporates cross-chain minting and burning capabilities, which are restricted to a `superchain_token_bridge` address. While the core ERC-20 functions operate as expected, the centralized control over token supply and individual balances by the `superchain_token_bridge` introduces significant economic and technical risks, as identified in the findings.

> **Final Recommendation:** Token holders should be fully aware of the centralized control exerted by the `superchain_token_bridge` address over the MAMO token supply and individual balances. It is crucial to understand the security measures and governance processes in place for this `superchain_token_bridge` address, as its compromise would have severe implications for the token's integrity and value. Consider implementing multi-signature control or time-locks for these highly privileged functions to mitigate risks associated with a single point of failure.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The MAMO token implements the ERC-20 standard, including extensions for burning, voting, and gasless permits (ERC-20Permit). The architecture (7.1) is standard for an ERC-20 token, inheriting from… |
| **Governance / Economics** | 1/10 | High | The economic model (7.4) of the MAMO token is heavily influenced by the `superchain_token_bridge` address. This address has the power to mint an arbitrary amount of new tokens via `crosschainMint`… |
| **Upgrades** | 2/10 | High | The MAMO contract is not implemented as an upgradeable proxy (7.7). Therefore, there are no upgrade-related risks or mechanisms to consider. Any changes to the contract's logic would require a new… |

## Security Findings

_🟠 1 High · 🟡 1 Medium · ⚪ 4 Informational_

### `CP-02` — Privileged Address Can Burn Tokens From Any Holder  *(Severity: High · Status: Unresolved)*

The `superchain_token_bridge` controller can destroy MAMO tokens from any holder's balance using the `crosschainBurn(address,uint256)` function. This means the controller could arbitrarily reduce the token holdings of any address, potentially leading to loss of user funds.

**Recommendation:** Token holders should be aware that the `superchain_token_bridge` address possesses the power to directly affect individual token balances. The integrity and trustworthiness of the `superchain_token_bridge` controller are paramount to prevent unauthorized token destruction. Strong access controls, such as a multi-signature wallet with a high threshold, are highly recommended for this critical function.


### `CP-01` — Privileged Address Can Mint New Tokens  *(Severity: Medium · Status: Unresolved)*

The `superchain_token_bridge` controller has the ability to create new MAMO tokens at any time using the `crosschainMint(address,uint256)` function. This action increases the total supply of MAMO, which could reduce the value of existing tokens held by others due to inflation.

**Recommendation:** Token holders should understand that the `superchain_token_bridge` address has significant control over the token supply. The security and governance of this `superchain_token_bridge` address are critical to the token's economic stability. Consider implementing safeguards like a multi-signature wallet or a time-lock for this function.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 90.0% of supply. What remains: 9.5% in wallets, 80.5% in other contracts. 72,482 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Mamo (MAMO), market cap $5M, rank #1755. Traded on Coinbase. 72,482 holders. Verified by: exchange listings.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $1.1M (DexScreener, all pools). 24h trading volume $1.4M (CoinGecko, all markets, daily snapshot). 24h trading volume $351K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $0.409 on 2026-08-27; the price is now 98.048% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $1.1M of DEX liquidity across 14 pools. Launch: 478 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x7300...19fe`](https://basescan.org/address/0x7300b37dfdfab110d83290a29dfb31b1740219fe) |
| **Network** | Base |
| **Price** | $0.00826 |
| **24h Volume** | $31.3K |
| **Liquidity** | $476.5K |
| **Volume / Liquidity** | 0.1× |
| **Token Age** | 1y |
| **Top-10 Holders** | 90.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 110 buys / 304 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0x4a021ba3ab1f0121e7df76f345c547db86cb3468)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/mamo-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-05*
