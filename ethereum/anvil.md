---
token: Anvil
ticker: ANVL
network: ethereum
risk_score: 8
status: low
date: 2026-10-07
---

# Anvil (ANVL) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 8/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/anvil-eth)

---

## Audit Summary

The Anvil contract implements a standard ERC-20 token with voting capabilities. The audit found no critical, high, or medium severity vulnerabilities. The contract adheres to established standards, features no privileged functions, and is not upgradeable, which simplifies its security profile. The overall risk level is assessed as Low.

> **Final Recommendation:** Given the contract's immutable nature and adherence to standard ERC-20 and voting token patterns, the primary recommendation is to ensure the initial token distribution and any off-chain governance processes are transparent and secure. For token holders, understanding the voting delegation mechanism is key. Continuous monitoring of the broader ecosystem for external threats or changes in dependency behavior is always prudent, although this contract has no explicit external dependencies.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The Anvil contract implements a standard ERC-20 token with additional voting capabilities (ERC20Votes). The architecture (7.1) is straightforward, adhering to established standards. Code security… |
| **Governance / Economics** | 9/10 | Low | The economic model (7.4) is based on a standard ERC-20 token, with no complex internal mechanisms or external dependencies that could introduce economic exploits. The contract incorporates voting… |
| **Upgrades** | 9/10 | Low | The Anvil contract is not implemented as an upgradeable proxy (7.7). This design choice eliminates all risks associated with upgrade mechanisms, such as proxy initialization issues, storage… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | 47.0% |
| **Top-3 Unlocked** | 75.9% |

## Security Findings

_🟡 1 Medium · ⚪ 5 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 8 address(es) other than the owner/deployer. No single one holds a majority: their exits thin the market rather than hand anyone the pool. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 23.1% of supply. What remains: 16.7% in wallets, 6.4% in other contracts. 3,420 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Anvil (ANVL), market cap $87M, rank #317. 3,420 holders. Verified by: CoinGecko.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $127K (DexScreener, all pools). 24h trading volume $418K (CoinGecko, all markets, daily snapshot). 24h trading volume $248K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $127K of DEX liquidity across 5 pools. Launch: 363 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xaeea...5597`](https://etherscan.io/address/0xaeeaa594e7dc112d67b8547fe9767a02c15b5597) |
| **Network** | Ethereum |
| **Price** | $0.001011 |
| **24h Volume** | $204.4K |
| **Liquidity** | $124.3K |
| **Volume / Liquidity** | 1.6× |
| **Token Age** | 1y |
| **Top-10 Holders** | 23.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 424 buys / 269 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0xdab309d2ee8a87d24679c3ba8d3b35ab8d99f55095859c2b67baf86012fdd857)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/anvil-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-07*
