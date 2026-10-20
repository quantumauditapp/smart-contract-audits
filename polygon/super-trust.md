---
token: SUPER TRUST
ticker: SUT
network: polygon
risk_score: 41
status: medium
date: 2026-10-20
---

# SUPER TRUST (SUT) — Smart Contract Security Analysis | Polygon

> **Risk Score: 41/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/super-trust-poly)

---

## Audit Summary

The SuperTrust contract is a standard ERC-20 token implementation with Pausable functionality. The ownership has been permanently renounced, meaning the administrative functions to pause or unpause transfers are now inaccessible. The architecture follows industry-standard OpenZeppelin patterns, ensuring robust token operations.

> **Final Recommendation:** The contract is secure and immutable. No further action is required as the administrative functions are permanently disabled.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes well-audited OpenZeppelin libraries for its core ERC-20 and Pausable logic. 7.1 Architecture is clean and follows standard inheritance patterns. 7.2 Code Security is high due to… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic and 7.5 Governance aspects are minimal as this is a standard utility token. There are no complex staking or lending mechanisms present. 7.6 External dependencies are limited to standard… |
| **Upgrades** | 8/10 | Low | 7.7 Upgrades are not supported as the contract is not a proxy. 7.8 Operations are stable and immutable. The renouncement of ownership ensures that no future logic changes can be introduced. |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 50.1% |
| **Top-3 Unlocked** | ⚠️ 99.7% |

## Security Findings

_🟡 1 Medium · ⚪ 5 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 4 address(es) other than the owner/deployer. One of them — a contract, 0xa741…0c2a — holds 50.2% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `CP-04` — Dormant Pause Functionality  *(Severity: Informational · Status: Unresolved)*

The contract includes pause and unpause functions that allow a privileged address to halt token transfers. Because ownership has been renounced, these functions are now permanently inaccessible and cannot be triggered.

**Recommendation:** No action required. The current state is safe as the risk of unauthorized pausing is eliminated.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 71.8% of supply. Of that, 21.0% burned — not holders that can sell, so excluded from the concentration score. What remains: 50.8% in wallets, 0.0% in other contracts. 53,290 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Super Trust (SUT). 53,290 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $60K (DexScreener, all pools). 24h trading volume $83K (CoinGecko, all markets, daily snapshot). 24h trading volume $35K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $14.10 on 2025-09-08; the price is now 98.4363% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $60K of DEX liquidity across 3 pools. Launch: 353 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x9896...ca55`](https://polygonscan.com/address/0x98965474ecbec2f532f1f780ee37b0b05f77ca55) |
| **Network** | Polygon |
| **Price** | $0.2032 |
| **24h Volume** | $34.7K |
| **Liquidity** | $59.9K |
| **Volume / Liquidity** | 0.6× |
| **Token Age** | 11mo |
| **Top-10 Holders** | 71.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 263 buys / 212 sells |

## Security Flags (4/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/polygon/0x092295c92bab5e734c4a60dbc0f0ffdcdfc4e165)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/super-trust-poly)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-20*
