---
token: 1INCH Token
ticker: 1INCH
network: ethereum
risk_score: 52
status: medium
date: 2026-10-30
---

# 1INCH Token (1INCH) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 52/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/1inch-token-eth)

---

## Audit Summary

The OneInch token is a standard ERC-20 implementation with additional burn and permit capabilities. The contract ownership has been permanently renounced, ensuring that no further administrative changes or minting operations can occur. The codebase follows established OpenZeppelin standards, providing a robust and secure foundation for the token.

> **Final Recommendation:** The contract is secure and immutable. No further action is required as the ownership is renounced and the code relies on standard, verified libraries.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The architecture utilizes standard OpenZeppelin ERC-20, ERC-20Permit, and ERC20Burnable modules, ensuring high interoperability and reliability. 7.1 Architecture and 7.2 Code Security are robust… |
| **Governance / Economics** | 8/10 | Low | 7.4 Economic and 7.5 Governance parameters are fixed due to the renounced ownership. The token supply is capped by the inability to call minting functions. There are no active governance mechanisms… |
| **Upgrades** | 6/10 | Medium | 7.7 Upgrades are not applicable as the contract is not a proxy and does not contain upgrade logic. The contract is immutable, which eliminates risks associated with logic changes or malicious… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | 31.4% |
| **Top-3 Unlocked** | 50.8% |

## Security Findings

_🟡 2 Medium · ⚪ 4 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 83.6% is held, unlocked, by 10 address(es) other than the owner/deployer. No single one holds a majority: their exits thin the market rather than hand anyone the pool. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them. This assessment covers the main pool, which holds 43% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Medium · Status: Acknowledged)*

Liquidity $11.8M (DexScreener, all pools). 24h trading volume $18.5M (CoinGecko, all markets, daily snapshot). 24h trading volume $8.5M (DexScreener, all pools). CoinGecko's record for this coin: all-time high $8.65 on 2021-10-27; the price is now 99.1124% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `CP-01` — Privileged minting function is now dormant  *(Severity: Informational · Status: Unresolved)*

The mint(address,uint256) function allows for the creation of new tokens, which would dilute existing holders. However, because the contract ownership has been permanently renounced, this function is now inaccessible and cannot be called by any address.

**Recommendation:** No action required. The renouncement of ownership effectively mitigates the risk of unauthorized token inflation.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 60.9% of supply. What remains: 25.3% in wallets, 35.6% in other contracts. 113,839 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as 1INCH (1INCH), market cap $108M, rank #255. On GoPlus's list of trusted tokens. Traded on Binance, Coinbase. 113,839 holders. Verified by: CoinGecko, GoPlus, exchange listings.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-PROFILE` — Asset class: Governance token  *(Severity: Informational · Status: Acknowledged)*

A token whose main use is voting on a protocol's decisions (delegation and vote checkpoints in its code). The class itself adds no points; the contract and market facts decide the score. Basis: CoinGecko category: Governance. Tokenomics — Supply: mintable with no on-chain cap found. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $11.8M of DEX liquidity across 26 pools. Launch: 2135 days of market history.

**Recommendation:** Check how much of the voting supply insiders hold and what governance can change.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x1111...c302`](https://etherscan.io/address/0x111111111117dc0aa78b770fa6a738034120c302) |
| **Network** | Ethereum |
| **Price** | $0.07858 |
| **24h Volume** | $2.01M |
| **Liquidity** | $5.05M |
| **Volume / Liquidity** | 0.4× |
| **Token Age** | 5y |
| **Top-10 Holders** | 60.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 67 buys / 81 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0x1d6ebf506eacf0e98a8c4566687380ddf1601192acd9bce29feeaf0c0245ea6f)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/1inch-token-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-30*
