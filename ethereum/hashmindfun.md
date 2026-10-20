---
token: Hashmind.fun
ticker: HASH
network: ethereum
risk_score: 20
status: low
date: 2026-10-15
---

# Hashmind.fun (HASH) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 20/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/hashmindfun-eth)

---

## Audit Summary

The HashmindToken contract is a standard ERC-20 token with permit functionality. The audit found no privileged functions, meaning no single entity can control or alter token transfers or supply. There are no identified vulnerabilities or central points of control, indicating a robust and decentralized design.

> **Final Recommendation:** Token holders should be aware that the HashmindToken contract is a standard, non-upgradeable ERC-20 token with no centralized control. This design minimizes administrative risks but also means that no entity can intervene to fix issues or recover lost funds if a user error occurs. Users should always exercise caution when interacting with blockchain transactions, verifying recipient addresses and amounts before confirming.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The HashmindToken contract implements a standard ERC-20 token with additional ERC-20 Permit functionality, inheriting from well-audited OpenZeppelin contracts. A significant strength is the complete… |
| **Governance / Economics** | 9/10 | Low | The economic and governance risk for HashmindToken is exceptionally low due to the absence of any centralized control mechanisms (7.4 Economic, 7.5 Governance). There are no owner-controlled… |
| **Upgrades** | 10/10 | Low | The HashmindToken contract is not implemented as a proxy and is therefore not upgradeable (7.7 Upgrades). This eliminates all risks associated with upgradeability, such as potential vulnerabilities… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Dead Address |

## Security Findings

_⚪ 7 Informational_

### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint capability, LP lock/burn state, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 40.4% of supply. What remains: 8.1% in wallets, 32.2% in other contracts. 319 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

319 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $46K (DexScreener, all pools). 24h trading volume $408K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $46K of DEX liquidity across 6 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xe780...1688`](https://etherscan.io/address/0xe7802782ac7679b4ff0e7106b3230adfef251688) |
| **Network** | Ethereum |
| **Price** | $0.0001294 |
| **24h Volume** | $404.7K |
| **Liquidity** | $45.1K |
| **Volume / Liquidity** | 9.0× |
| **Token Age** | 17h |
| **Top-10 Holders** | 40.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1452 buys / 924 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x5df8e8d882caf8d462e285c78d181149c36582d3b6261478da10c6336637596c)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/hashmindfun-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-15*
