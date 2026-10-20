---
token: apxUSD
ticker: APXUSD
network: ethereum
risk_score: 12
status: low
date: 2026-10-09
---

# apxUSD (APXUSD) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 12/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/apxusd-eth)

---

## Audit Summary

The ApxUSD token contract is an upgradeable ERC-20 token with features such as pausing, a deny list, supply capping, and minting/burning capabilities. The contract utilizes the UUPS proxy pattern and an AccessManaged system for role-based access control. No critical or high-severity vulnerabilities were identified in the provided code. The primary risks stem from the centralized control inherent in its design, which grants significant power to administrative roles.

> **Final Recommendation:** It is recommended to implement robust multi-signature or time-locked mechanisms for all privileged operations, especially those related to upgrades, minting, pausing, and managing the deny list. This decentralizes control and adds a layer of security against single points of failure or compromise of administrative keys. Additionally, a comprehensive emergency response plan should be in place for scenarios requiring the use of pause or deny list functionalities.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 9/10 | Low | The ApxUSD contract is an ERC-20 token implementing standard functionalities for transfers, approvals, and balances (7.2 Code Security). It leverages well-audited OpenZeppelin libraries for features… |
| **Governance / Economics** | 9/10 | Low | The contract design incorporates significant centralized control over key token functionalities (7.4 Economic). An authorized entity can mint new tokens, pause all transfers, and add addresses to a… |
| **Upgrades** | 5/10 | Medium | The ApxUSD token uses the UUPS (Universal Upgradeable Proxy Standard) pattern, allowing the contract logic to be upgraded in the future (7.7 Upgrades). This provides flexibility for bug fixes or… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Uups |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_⚪ 6 Informational_

### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 92.6% of supply. What remains: 1.8% in wallets, 90.7% in other contracts. 1,864 holders in total. For a verified reference asset the largest holders are custodians, exchanges and bridges; concentration is reported, not scored.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as apxUSD (APXUSD), market cap $315M, rank #144. 1,864 holders. Verified by: CoinGecko.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $37.0M (DexScreener, all pools). 24h trading volume $8.1M (CoinGecko, all markets, daily snapshot). 24h trading volume $8.1M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-POWERS` — What the token's controller can do  *(Severity: Informational · Status: Acknowledged)*

The contract lets its controller — an owner that could not be resolved — mint new supply; pause all transfers. These are the issuer's controls by design; for a verified issuer they are counterparty risk — the issuer can act on any holder, including you.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-PROFILE` — Asset class: Stablecoin  *(Severity: Informational · Status: Acknowledged)*

A token designed to hold a fixed value (usually $1). Its safety rests on what backs it and on who can mint, freeze or pause it. Scored as an established reference asset: its identity is verified, so the issuer's or protocol's controls (listed as findings) are real and are priced once as counterparty risk, and LP locks and holder concentration are not scored — its pools belong to market makers and its largest holders are exchanges, bridges and custody. Basis: CoinGecko category: Stablecoins. Tokenomics — Supply: issued and redeemed by the issuer against its backing. Control: an owner that could not be resolved. Code: upgradeable proxy. Fees: no buy or sell tax. Market: $37.0M of DEX liquidity across 14 pools. Launch: 228 days of market history.

**Recommendation:** Check what backs the peg and who controls supply: reserve attestations for an issuer-backed coin, collateral and governance for a protocol coin.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x98a8...4665`](https://etherscan.io/address/0x98a878b1cd98131b271883b390f68d2c90674665) |
| **Network** | Ethereum |
| **Price** | $0.9907 |
| **24h Volume** | $1.82M |
| **Liquidity** | $10.12M |
| **Volume / Liquidity** | 0.2× |
| **Token Age** | 7mo |
| **Top-10 Holders** | 92.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 79 buys / 87 sells |

## Security Flags (1/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0x9f2d9491277a9f2551c1f7533c1789aa6023bba0c5e9397e8a019cac5c10fe7f)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/apxusd-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-09*
