---
token: Telcoin (PoS)
ticker: TEL
network: polygon
risk_score: 30
status: low
date: 2026-10-20
---

# Telcoin (PoS) (TEL) — Smart Contract Security Analysis | Polygon

> **Risk Score: 30/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/telcoin-pos-poly)

---

## Audit Summary

The UChildERC20Proxy contract serves as a standard upgradeable proxy pattern on the Polygon network. The architecture relies on a centralized owner to manage implementation updates and proxy ownership. No vulnerabilities were identified in the provided code map, as the logic strictly adheres to standard proxy delegation patterns.

> **Final Recommendation:** The contract is well-structured for its intended purpose as a proxy. To improve security, transition the proxy ownership from a single EOA to a multi-signature wallet or a decentralized governance contract to mitigate the risk of a single point of failure.

Ensure that any future implementation upgrades are thoroughly tested on a testnet environment before deployment to mainnet. Maintain strict operational security regarding the private keys associated with the proxy owner role.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The architecture follows a standard proxy pattern (7.1 Architecture) ensuring clear separation between proxy state and implementation logic. Code security (7.2) is maintained through simple… |
| **Governance / Economics** | 1/10 | High | Economic risk (7.4) is primarily tied to the centralization of the proxy owner. Governance (7.5) is currently handled by a single address, which represents a single point of failure. Operations (7.8)… |
| **Upgrades** | 5/10 | Medium | The upgrade mechanism (7.7) is robust, utilizing a standard implementation swap pattern. The updateAndCall function allows for atomic upgrades and initialization, which is a best practice for… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 73.6% |
| **Top-3 Unlocked** | ⚠️ 94.2% |

## Security Findings

_🟡 1 Medium · ⚪ 5 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 99.4% is held, unlocked, by 10 address(es) other than the owner/deployer. One of them — a contract, 0x84b3…eacd — holds 73.6% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them. This assessment covers the main pool, which holds 19% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 63.7% of supply. What remains: 9.1% in wallets, 54.6% in other contracts. 33,309 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Telcoin [OLD] (TEL). 33,309 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $441K (DexScreener, all pools). 24h trading volume $227K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mint capability could not be read. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $441K of DEX liquidity across 30 pools. Launch: 2060 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xdf78...cc32`](https://polygonscan.com/address/0xdf7837de1f2fa4631d716cf2502f8b230f1dcc32) |
| **Network** | Polygon |
| **Price** | $0.001502 |
| **24h Volume** | $66.0K |
| **Liquidity** | $82.3K |
| **Volume / Liquidity** | 0.8× |
| **Token Age** | 5y |
| **Top-10 Holders** | 63.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1299 buys / 655 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ⚠️ Unknown |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/polygon/0x3bd8a254163f8328efcc4f8c36da566753462433)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/telcoin-pos-poly)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-20*
