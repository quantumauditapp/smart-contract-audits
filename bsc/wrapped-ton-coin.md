---
token: Wrapped TON Coin
ticker: TONCOIN
network: bsc
risk_score: 21
status: low
date: 2026-10-01
---

# Wrapped TON Coin (TONCOIN) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 21/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/wrapped-ton-coin-bsc)

---

## Audit Summary

The audited Bridge token contract implements standard ERC-20 functionality without any identified critical or high-severity vulnerabilities. A key characteristic is the complete absence of privileged functions, meaning no single entity can alter core token behavior or transfer mechanisms. This design promotes decentralization and reduces central point of failure risks.

> **Final Recommendation:** Given the immutable nature and lack of privileged control within this token contract, security recommendations primarily focus on external interactions. Ensure that any external systems or bridge components interacting with this token are robustly secured and thoroughly audited. Pay close attention to the security of the bridge's minting and burning mechanisms, as these would be the primary vectors for supply manipulation. Regular monitoring of the contract's activity on the blockchain is also advised.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract implements the ERC-20 standard, providing `transfer` and `transferFrom` functions for token movement. A significant strength is the absence of any privileged functions, ensuring that no… |
| **Governance / Economics** | 7/10 | Low | The economic model of this token contract is straightforward, adhering to the ERC-20 standard without complex internal mechanisms. Crucially, there are no governance or administrative functions that… |
| **Upgrades** | 6/10 | Medium | The contract is not implemented as a proxy and therefore is not upgradeable (7.7 Upgrades). This design choice ensures immutability of the contract's logic, providing a high degree of certainty… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 92.2% |
| **Top-3 Unlocked** | ⚠️ 97.0% |

## Security Findings

_🟡 2 Medium · ⚪ 5 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 99.5% is held, unlocked, by 10 address(es) other than the owner/deployer. One of them — a wallet, 0x4101…1ac1 — holds 92.2% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them. This assessment covers the main pool, which holds 25% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-POWERS` — What the token's controller can do  *(Severity: Medium · Status: Acknowledged)*

The contract lets its controller — an owner that could not be resolved — mint new supply. Nothing independent vouches for whoever holds them, so each is a live risk to holders.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 10.1% of supply. Of that, 1.9% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 8.2% in wallets, 0.0% in other contracts. 119,561 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Gram (prev. Toncoin) (GRAM), market cap $4.2B, rank #33. Traded on Binance. 119,561 holders. Verified by: CoinGecko, exchange listings.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $227K (DexScreener, all pools). 24h trading volume $62.7M (CoinGecko, all markets, daily snapshot). 24h trading volume $917K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $227K of DEX liquidity across 30 pools. Launch: 1823 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x76a7...220f`](https://bscscan.com/address/0x76a797a59ba2c17726896976b7b3747bfd1d220f) |
| **Network** | BNB Chain |
| **Price** | $1.5600 |
| **24h Volume** | $391.5K |
| **Liquidity** | $57.0K |
| **Volume / Liquidity** | 6.9× |
| **Token Age** | 5y |
| **Top-10 Holders** | 10.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2574 buys / 2686 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x819a26d0c6f3af2b9fe4e9c4bcac04fcb3ea7f2a)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/wrapped-ton-coin-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-01*
