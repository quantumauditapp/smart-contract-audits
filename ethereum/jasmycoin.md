---
token: JasmyCoin
ticker: JASMY
network: ethereum
risk_score: 16
status: low
date: 2026-10-01
---

# JasmyCoin (JASMY) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 16/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/jasmycoin-eth)

---

## Audit Summary

The JasmyCoin contract implements a standard ERC-20 token with no additional complex logic or privileged functions. The audit found no critical, high, medium, or low-severity vulnerabilities. The contract adheres closely to the ERC-20 standard, minimizing potential attack vectors.

> **Final Recommendation:** The JasmyCoin contract is a robust and standard ERC-20 implementation. Given its simplicity and lack of complex features, the primary recommendation is to ensure that any external systems interacting with this token correctly handle standard ERC-20 behaviors, particularly regarding approvals and allowances. Token holders should remain vigilant about phishing attempts and only interact with trusted interfaces.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The JasmyCoin contract is a straightforward implementation of the ERC-20 standard (7.1 Architecture). It includes all required ERC-20 functions like `transfer` and `transferFrom`, which operate as… |
| **Governance / Economics** | 8/10 | Low | The contract exhibits a low governance and economic risk profile due to its simplicity. There are no governance mechanisms, such as voting or multi-signature controls, built into the contract itself… |
| **Upgrades** | 9/10 | Low | The JasmyCoin contract is not designed with upgradeability features, such as proxy patterns (7.7 Upgrades). This means the contract's logic is immutable once deployed, eliminating any risks… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | 31.6% |
| **Top-3 Unlocked** | 74.3% |

## Security Findings

_🟡 2 Medium · ⚪ 4 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 99.9% is held, unlocked, by 10 address(es) other than the owner/deployer. No single one holds a majority: their exits thin the market rather than hand anyone the pool. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them. This assessment covers the main pool, which holds 40% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Medium · Status: Acknowledged)*

Liquidity $95K (DexScreener, all pools). 24h trading volume $14.8M (CoinGecko, all markets, daily snapshot). 24h trading volume $52K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $4.79 on 2021-02-15; the price is now 99.8933% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 47.6% of supply. What remains: 47.6% in wallets, 0.0% in other contracts. The deployer/owner wallet itself holds 1.1%. 100,263 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as JasmyCoin (JASMY), market cap $253M, rank #166. Traded on Binance, Coinbase. 100,263 holders. Verified by: CoinGecko, exchange listings.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $95K of DEX liquidity across 12 pools. Launch: 1548 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x7420...03ec`](https://etherscan.io/address/0x7420b4b9a0110cdc71fb720908340c03f9bc03ec) |
| **Network** | Ethereum |
| **Price** | $0.005989 |
| **24h Volume** | $34.5K |
| **Liquidity** | $38.6K |
| **Volume / Liquidity** | 0.9× |
| **Token Age** | 4y |
| **Top-10 Holders** | 47.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 85 buys / 71 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x4d1eff861316396dd1915f69b49f4c2d7b11590d)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/jasmycoin-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-01*
