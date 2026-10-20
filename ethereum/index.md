---
token: Index
ticker: INDEX
network: ethereum
risk_score: 25
status: low
date: 2026-10-17
---

# Index (INDEX) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 25/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/index-eth)

---

## Audit Summary

The IndexToken contract implements core ERC-20 functionalities. Static analysis revealed no critical or high-severity vulnerabilities. The contract lacks a `totalSupply()` function, which is a deviation from the ERC-20 standard, but otherwise appears robust.

> **Final Recommendation:** Ensure all standard ERC-20 functions, including `totalSupply()`, are implemented for full compatibility and expected behavior across various platforms and integrations. Consider implementing a robust testing suite, including unit and integration tests, to cover all critical functionalities and edge cases.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The IndexToken contract provides basic ERC-20 token functionality, including `transfer` and `transferFrom`. It utilizes `safe96` for amount handling, mitigating potential integer overflow/underflow… |
| **Governance / Economics** | 1/10 | High | The contract exhibits a decentralized control structure with no privileged functions or roles that can directly alter token transfer logic or economic parameters (7.3 Access Control, 7.4 Economic).… |
| **Upgrades** | 8/10 | Low | The IndexToken contract is not designed as an upgradeable proxy (7.7 Upgrades). This means its logic is immutable once deployed, eliminating upgrade-related risks such as proxy misconfigurations or… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 57.8% |
| **Top-3 Unlocked** | ⚠️ 99.9% |

## Security Findings

_🟡 2 Medium · ⚪ 4 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 3 address(es) other than the owner/deployer. One of them — a contract, 0x3887…7f1c — holds 57.8% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them. This assessment covers the main pool, which holds 89% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Medium · Status: Acknowledged)*

Liquidity $153K (DexScreener, all pools). 24h trading volume $3.5M (CoinGecko, all markets, daily snapshot). 24h trading volume $151K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $67.08 on 2021-05-08; the price is now 99.5565% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 77.8% of supply. Of that, 10.0% burned — not holders that can sell, so excluded from the concentration score. What remains: 33.6% in wallets, 34.2% in other contracts. 5,962 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Index Cooperative (INDEX), market cap $2M, rank #2288. Traded on Coinbase. 5,962 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-PROFILE` — Asset class: Governance token  *(Severity: Informational · Status: Acknowledged)*

A token whose main use is voting on a protocol's decisions (delegation and vote checkpoints in its code). The class itself adds no points; the contract and market facts decide the score. Basis: CoinGecko category: Governance. Tokenomics — Supply: fixed — the contract has no mint function. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $153K of DEX liquidity across 11 pools. Launch: 2201 days of market history.

**Recommendation:** Check how much of the voting supply insiders hold and what governance can change.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x0954...4cab`](https://etherscan.io/address/0x0954906da0bf32d5479e25f46056d22f08464cab) |
| **Network** | Ethereum |
| **Price** | $0.3526 |
| **24h Volume** | $146.3K |
| **Liquidity** | $135.6K |
| **Volume / Liquidity** | 1.1× |
| **Token Age** | 6y |
| **Top-10 Holders** | 77.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 292 buys / 278 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x2bd7146e038cbba3e15a02b5e60fd05d4c4a50d2f755d9f87517e7b00f633aa2)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/index-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-17*
