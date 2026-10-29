---
token: GTA Pepe
ticker: GTAPEPE
network: ethereum
risk_score: 47
status: medium
date: 2026-10-29
---

# GTA Pepe (GTAPEPE) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 47/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/gta-pepe-eth)

---

## Audit Summary

The GTAPEPE token is a standard ERC-20 implementation. The audit identified a critical flaw in the transfer logic where the contract fails to properly handle return values in specific trading limit functions, potentially causing integration issues with decentralized exchanges. The contract lacks administrative control functions, which ensures immutability but prevents emergency intervention.

> **Final Recommendation:** The developer should immediately refactor the trading limit functions to ensure they correctly return boolean values as expected by standard ERC-20 interfaces. This will prevent potential failures when interacting with automated market makers or other DeFi protocols.

Given the lack of administrative functions, ensure all deployment parameters are verified before launch, as no post-deployment adjustments are possible. Users should be aware that the current implementation may cause transaction failures on certain platforms due to the identified return value bug.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The architecture follows standard OpenZeppelin ERC-20 patterns, providing a reliable foundation for token transfers. The code is clean and adheres to modern Solidity standards (0.8.23). However, the… |
| **Governance / Economics** | 8/10 | Low | The token has no governance or administrative functions, meaning the economic parameters are fixed at deployment. This eliminates risks associated with centralized rug-pulls or malicious owner… |
| **Upgrades** | 8/10 | Low | The contract is not a proxy and does not support upgrades. This ensures that the code cannot be altered post-deployment, providing high security against malicious logic changes. Users can rely on the… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Dead Address |

## Security Findings

_🟠 1 High · ⚪ 6 Informational_

### `CD-01` — Incorrect Return Values in Trading Logic  *(Severity: High · Status: Unresolved)*

The functions MAxTradingIdentifierLimits, _transfer, returnTx, transfer, and transferFrom contain logic that fails to correctly return the expected boolean values required by the ERC-20 standard. This can cause external contracts, such as decentralized exchanges, to incorrectly interpret the success or failure of a token transfer.

**Recommendation:** Update the affected functions to explicitly return 'true' upon successful execution and ensure all internal logic paths conform to the ERC-20 interface specification.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 42.1% of supply. What remains: 16.5% in wallets, 25.7% in other contracts. 176 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

176 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $19K (DexScreener, all pools). 24h trading volume $35K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: meme vocabulary in name/ticker (pepe). Tokenomics — Supply: fixed — the contract has no mint function. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $19K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x3034...5493`](https://etherscan.io/address/0x3034f5fcabf9af1ccca850b2175720327c105493) |
| **Network** | Ethereum |
| **Price** | $0.00004717 |
| **24h Volume** | $35.2K |
| **Liquidity** | $18.6K |
| **Volume / Liquidity** | 1.9× |
| **Token Age** | 2h |
| **Top-10 Holders** | 42.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 254 buys / 189 sells |

## Security Flags (4/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0xc0a4317e7f24e172c48631d84ace055b26e4341707cf38b7e2b0d1f8805f119c)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/gta-pepe-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-29*
