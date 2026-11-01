---
token: LaowuCoin
ticker: 老吴
network: bsc
risk_score: 40
status: medium
date: 2026-11-01
---

# LaowuCoin (老吴) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 40/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/laowucoin-bsc)

---

## Audit Summary

The FlapTaxTokenV3 is an EIP-1167 minimal clone token. The contract ownership has been renounced, effectively locking the administrative functions startMigration and finalizeMigration. As these functions are no longer callable, the protocol state is immutable. The architecture follows standard ERC-20 patterns with additional tax and anti-farmer logic.

> **Final Recommendation:** The protocol is in a stable, immutable state due to the renouncement of ownership. No further administrative actions are required or possible. Users should be aware that the current tax and anti-farmer logic is permanent and cannot be adjusted by any party.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes standard OpenZeppelin upgradeable libraries to implement a secure ERC-20 token. 7.1 Architecture: EIP-1167 minimal clone ensures low deployment costs and fixed logic. 7.2 Code… |
| **Governance / Economics** | 5/10 | Medium | 7.4 Economic: The token incorporates tax and anti-farmer mechanisms that are now locked in their current state. 7.5 Governance: Governance is effectively non-existent as ownership is renounced. 7.8… |
| **Upgrades** | 8/10 | Low | 7.7 Upgrades: The contract is deployed as an EIP-1167 minimal clone, which is immutable by design. There is no proxy upgrade mechanism present, and the implementation address cannot be changed. This… |

## Security Findings

_🟠 1 High · ⚪ 5 Informational_

### `QA-HOLDERS` — Who holds the supply  *(Severity: High · Status: Acknowledged)*

The ten largest holders own 49.3% of supply. What remains: 7.6% in wallets, 41.7% in other contracts. The deployer/owner wallet itself holds 30.0%. A holder that also controls the contract can sell into its own liquidity. 366 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint/owner authority, mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

366 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $12K (DexScreener, all pools). 24h trading volume $383K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: 0% on buy, 0.99% on sell. Market: $12K of DEX liquidity across 2 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xdf8a...7777`](https://bscscan.com/address/0xdf8a2cccbff4a15616fc4ea6fd3574645d317777) |
| **Network** | BNB Chain |
| **Price** | $0.00001682 |
| **24h Volume** | $349.4K |
| **Liquidity** | $11.8K |
| **Volume / Liquidity** | 29.5× |
| **Token Age** | 1h |
| **Top-10 Holders** | 49.3% of supply |
| **Buy / Sell Tax** | 0.0% / 1.0% |
| **24h Transactions** | 3223 buys / 3180 sells |

## Security Flags (4/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ⚠️ Unknown |
| Not Upgradeable | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| Not Upgradeable | ✅ | Minimal proxy clone — the implementation is fixed in its bytecode and cannot be swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0xd6586013d4c7be56f634346a111b661b31a1f322)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/laowucoin-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-01*
