---
token: GRVT
ticker: GRVT
network: ethereum
risk_score: 21
status: low
date: 2026-10-21
---

# GRVT (GRVT) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 21/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/grvt-eth)

---

## Audit Summary

The GRVTToken is a standard ERC-20 implementation utilizing OpenZeppelin libraries for permit functionality and burnability. The contract follows industry-standard patterns with no centralized administrative privileges or restricted access control mechanisms. The code is clean, modular, and adheres to established security practices for token contracts.

> **Final Recommendation:** The contract is secure and follows best practices for a standard ERC-20 token. No further action is required for the smart contract code itself. Ensure that any future integrations or UI interactions correctly handle the ERC-20 permit functionality to improve user experience.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The architecture follows a standard ERC-20 implementation (7.1 Architecture) utilizing well-audited OpenZeppelin contracts (7.2 Code Security). There are no custom logic paths or complex state… |
| **Governance / Economics** | 6/10 | Medium | The token contract does not implement governance or economic parameters (7.4 Economic, 7.5 Governance). It functions as a pure utility token without internal minting or fee mechanisms. Operations are… |
| **Upgrades** | 9/10 | Low | The contract is not upgradeable (7.7 Upgrades). It is deployed as a standalone, immutable contract. No proxy patterns or administrative upgrade functions are present. |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 1 Medium · ⚪ 5 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a wallet, 0x007c…dc48 — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them. This assessment covers the main pool, which holds 66% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 93.3% of supply. What remains: 5.1% in wallets, 88.2% in other contracts. 1,381 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as GRVT Token (GRVT), market cap $31M, rank #649. 1,381 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $1.5M (DexScreener, all pools). 24h trading volume $26.4M (CoinGecko, all markets, daily snapshot). 24h trading volume $1.7M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $1.5M of DEX liquidity across 4 pools. Launch: 82 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xad29...17cf`](https://etherscan.io/address/0xad29f2723fcdbcf665f210f25e06f97477e417cf) |
| **Network** | Ethereum |
| **Price** | $0.2592 |
| **24h Volume** | $1.38M |
| **Liquidity** | $978.3K |
| **Volume / Liquidity** | 1.4× |
| **Token Age** | 2mo |
| **Top-10 Holders** | 93.3% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 400 buys / 585 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0x73ee8d69931d35ba2b024a4abe7f789eef9f8547d7aff8c31d3b5cf3f9193158)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/grvt-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-21*
