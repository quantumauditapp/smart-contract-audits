---
token: Treasure
ticker: MAGIC
network: ethereum
risk_score: 46
status: medium
date: 2026-10-10
---

# Treasure (MAGIC) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 46/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/treasure-eth)

---

## Audit Summary

The MagicTIP39Facet contract, part of a Diamond proxy system, implements standard ERC-20 token functionality. No critical or high-severity vulnerabilities were identified. The contract's core token transfer mechanisms are standard and do not include any owner-controlled functions that could alter token behavior or supply.

> **Final Recommendation:** It is recommended to maintain robust security practices for the Diamond proxy's upgrade mechanism, ensuring that all future facet deployments and upgrades undergo thorough testing and auditing. Implement strict access controls for the multisig controlling upgrades, and consider time-locks for critical upgrade operations to provide a window for community review and emergency response. Continuous monitoring of the contract and its interactions within the broader protocol is also advised.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The MagicTIP39Facet contract provides standard ERC-20 token functionality, including `transfer` and `transferFrom` functions, which operate as expected (7.2 Code Security). The implementation is… |
| **Governance / Economics** | 1/10 | High | This facet does not contain any owner-controlled functions that could manipulate token supply, freeze transfers, or alter core economic parameters (7.4 Economic). While the system owner is a multisig… |
| **Upgrades** | 1/10 | High | The MagicTIP39Facet is deployed as part of a Diamond proxy pattern, allowing for modular and flexible upgrades (7.1 Architecture). This pattern enables future enhancements and bug fixes without… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Diamond |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 73.8% |
| **Top-3 Unlocked** | ⚠️ 97.5% |

## Security Findings

_🟡 1 Medium · ⚪ 5 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 6 address(es) other than the owner/deployer. One of them — a contract, 0x2dde…d273 — holds 73.8% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint/owner authority, mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 94.0% of supply. What remains: 0.9% in wallets, 93.2% in other contracts. 5,723 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Treasure (MAGIC), market cap $54M, rank #458. Traded on Binance. 5,723 holders. Verified by: CoinGecko.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $21K (DexScreener, all pools). 24h trading volume $408.7M (CoinGecko, all markets, daily snapshot). 24h trading volume $169K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $6.32 on 2022-02-19; the price is now 97.4721% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: a 3-of-6 multisig. Code: upgradeable proxy. Fees: no buy or sell tax. Market: $21K of DEX liquidity across 3 pools. Launch: 1859 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xb0c7...ac9a`](https://etherscan.io/address/0xb0c7a3ba49c7a6eaba6cd4a96c55a1391070ac9a) |
| **Network** | Ethereum |
| **Price** | $0.1091 |
| **24h Volume** | $44.0K |
| **Liquidity** | $21.1K |
| **Volume / Liquidity** | 2.1× |
| **Token Age** | 5y |
| **Top-10 Holders** | 94.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 329 buys / 275 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0x8c56ca4f7eb12a7c217bbe36cc427a9dcb66f590)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/treasure-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-10*
