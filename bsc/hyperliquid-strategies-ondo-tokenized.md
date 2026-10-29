---
token: Hyperliquid Strategies (Ondo Tokenized)
ticker: PURRON
network: bsc
risk_score: 11
status: low
date: 2026-10-29
---

# Hyperliquid Strategies (Ondo Tokenized) (PURRON) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 11/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/hyperliquid-strategies-ondo-tokenized-bsc)

---

## Audit Summary

The contract is a standard BeaconProxy implementation designed to delegate calls to an implementation contract defined by a beacon. The codebase follows established OpenZeppelin patterns for proxy architecture. No business logic or token functionality is present within this contract, as it serves purely as a transparent proxy layer.

> **Final Recommendation:** Maintain the current implementation as it adheres to industry-standard proxy patterns. Ensure that the beacon contract and the implementation contracts it points to undergo rigorous security audits, as the security of this proxy is entirely dependent on those external components.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The architecture utilizes a standard BeaconProxy pattern, ensuring modularity and separation of concerns. 7.1 Architecture is robust, relying on well-tested ERC1967 storage slots to prevent… |
| **Governance / Economics** | 10/10 | Low | 7.4 Economic and 7.5 Governance factors are not applicable as this contract contains no internal state variables or logic governing tokenomics or administrative voting. The contract acts strictly as… |
| **Upgrades** | 5/10 | Medium | 7.7 Upgrades are managed via the beacon contract, which is the industry standard for proxy-based upgradeability. This allows for seamless implementation updates without changing the proxy address.… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 95.5% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_⚪ 6 Informational_

### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 93.7% of supply. Of that, 18.8% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 58.8% in wallets, 16.1% in other contracts. 482 holders in total. For a verified reference asset the largest holders are custodians, exchanges and bridges; concentration is reported, not scored.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Hyperliquid Strategies (Ondo Tokenized) (PURRON), rank #6090. Its admin (0x8860…3b26) controls 440 issuer-backed coins CoinGecko lists on bsc, $1.1B together, among them Circle Internet Group (Ondo Tokenized Stock), Ondo U.S. Dollar Token, iShares Core S&P 500 ETF (Ondo Tokenized ETF): one issuer's programme, read on-chain. 482 holders. Verified by: issuer programme.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $57K (DexScreener, all pools). 24h trading volume $52 (CoinGecko, all markets, daily snapshot). 24h trading volume $955K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Tokenized real-world asset  *(Severity: Informational · Status: Acknowledged)*

A token backed by an off-chain asset (a stock, gold, treasury bills, a fund share) held by a named issuer or custodian. Issuance, redemption and transfer restrictions are the issuer's by design. Scored as an established reference asset: its identity is verified, so the issuer's or protocol's controls (listed as findings) are real and are priced once as counterparty risk, and LP locks and holder concentration are not scored — its pools belong to market makers and its largest holders are exchanges, bridges and custody. Basis: CoinGecko category: Tokenized Stocks. Tokenomics — Supply: mint capability could not be read. Control: an owner that could not be resolved. Code: upgradeable proxy. Fees: no buy or sell tax. Market: $57K of DEX liquidity across 30 pools. Launch: under a day of market history.

**Recommendation:** Treat the issuer or custodian as the counterparty: check its custody reports and who may hold or redeem the token.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x89cc...0601`](https://bscscan.com/address/0x89cc700f308a4c59889fbf3286216554c53b0601) |
| **Network** | BNB Chain |
| **Price** | $12.1000 |
| **24h Volume** | $955.3K |
| **Liquidity** | $56.7K |
| **Volume / Liquidity** | 16.9× |
| **Token Age** | 5h |
| **Top-10 Holders** | 93.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 4770 buys / 4869 sells |

## Security Flags (1/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ⚠️ Unknown |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x47897b86b78054d0dbd7c7b6a0fc4bec9ee839ba)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/hyperliquid-strategies-ondo-tokenized-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-29*
