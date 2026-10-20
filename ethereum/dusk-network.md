---
token: Dusk Network
ticker: DUSK
network: ethereum
risk_score: 30
status: low
date: 2026-10-11
---

# Dusk Network (DUSK) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 30/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/dusk-network-eth)

---

## Audit Summary

The DuskToken contract is a standard ERC-20 implementation. The audit found no critical, high, medium, or low severity issues. The contract adheres to basic ERC-20 functionality without additional complex features or privileged roles, indicating a robust and secure design for its intended purpose.

> **Final Recommendation:** The DuskToken contract is a well-implemented, standard ERC-20 token with no identified vulnerabilities. For future deployments, ensure thorough testing across all supported EVM networks. Maintain vigilance regarding external dependencies and user interactions, as even robust contracts can be affected by external factors. Consider formal verification for critical components if additional assurance is desired.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The DuskToken contract is a straightforward implementation of the ERC-20 standard (7.1 Architecture). The core transfer logic, including `transfer` and `transferFrom`, correctly handles token… |
| **Governance / Economics** | 5/10 | Medium | The DuskToken contract does not incorporate any governance mechanisms or complex economic models (7.5 Governance). Its design as a pure ERC-20 token means there are no internal economic parameters or… |
| **Upgrades** | 9/10 | Low | The contract is not designed as an upgradeable proxy (7.7 Upgrades), as indicated by `is_proxy: false`. This eliminates the risks associated with upgrade mechanisms, such as proxy misconfigurations… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 50.9% |
| **Top-3 Unlocked** | ⚠️ 99.2% |

## Security Findings

_🟡 1 Medium · ⚪ 5 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 4 address(es) other than the owner/deployer. One of them — a wallet, 0x2607…47cb — holds 50.9% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them. This assessment covers the main pool, which holds 50% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 82.1% of supply. What remains: 35.8% in wallets, 46.2% in other contracts. 20,121 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as DUSK (DUSK), market cap $52M, rank #473. Traded on Binance. 20,121 holders. Verified by: CoinGecko, exchange listings.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $546K (DexScreener, all pools). 24h trading volume $9.7M (CoinGecko, all markets, daily snapshot). 24h trading volume $109K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $1.09 on 2021-12-29; the price is now 92.1483% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $546K of DEX liquidity across 3 pools. Launch: 1983 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x940a...a551`](https://etherscan.io/address/0x940a2db1b7008b6c776d4faaca729d6d4a4aa551) |
| **Network** | Ethereum |
| **Price** | $0.08737 |
| **24h Volume** | $99.6K |
| **Liquidity** | $274.5K |
| **Volume / Liquidity** | 0.4× |
| **Token Age** | 5y |
| **Top-10 Holders** | 82.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 286 buys / 261 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0xff29d3e552155180809ea3a877408a4620058086)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/dusk-network-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-11*
