---
token: The McRib Indicator
ticker: MCRIB
network: ethereum
risk_score: 64
status: medium
date: 2026-10-23
---

# The McRib Indicator (MCRIB) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 64/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/the-mcrib-indicator-eth)

---

## Audit Summary

The BaseToken contract is a standard ERC-20 implementation utilizing OpenZeppelin libraries. Ownership has been permanently renounced, ensuring no administrative backdoors or privileged control exists. The codebase is clean, follows industry standards, and exhibits no critical vulnerabilities.

> **Final Recommendation:** The contract is secure and ready for deployment. No further modifications are required as the ownership renouncement provides the highest level of trust for token holders.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The architecture follows the standard ERC-20 pattern with Burnable extensions, ensuring high interoperability. 7.1 Architecture is sound, utilizing modular OpenZeppelin components. 7.2 Code Security… |
| **Governance / Economics** | 2/10 | High | 7.4 Economic and 7.5 Governance factors are neutral as the token lacks internal minting or governance mechanisms. 7.6 External dependencies are limited to standard OpenZeppelin contracts, which are… |
| **Upgrades** | 8/10 | Low | 7.7 Upgrades are not supported as the contract is not a proxy. 7.8 Operations are simplified by the lack of administrative functions. The contract is immutable, providing long-term stability for… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · ⚪ 6 Informational_

### `QA-LIQUIDITY` — Liquidity withdrawable by the owner/deployer  *(Severity: High · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by the token's owner/deployer (0x7050…c623) — they can pull that liquidity at any moment. This is the rug-pull path. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint/owner authority, mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 19.7% of supply. What remains: 5.7% in wallets, 14.0% in other contracts. 390 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

390 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $102K (DexScreener, all pools). 24h trading volume $879K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $102K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x1b70...1bf1`](https://etherscan.io/address/0x1b7049760f4cd739df63673b74e2f191709b1bf1) |
| **Network** | Ethereum |
| **Price** | $0.00041 |
| **24h Volume** | $878.8K |
| **Liquidity** | $101.5K |
| **Volume / Liquidity** | 8.7× |
| **Token Age** | 6h |
| **Top-10 Holders** | 19.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1530 buys / 888 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x3bd4ac0cdf5662be33d30d7517105a5eb6898e1a22e28982bd0b39cb67c96aaf)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/the-mcrib-indicator-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-23*
