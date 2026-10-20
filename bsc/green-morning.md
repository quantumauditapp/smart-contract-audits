---
token: GREEN MORNING
ticker: GM
network: bsc
risk_score: 9
status: low
date: 2026-10-06
---

# GREEN MORNING (GM) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 9/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/green-morning-bsc)

---

## Audit Summary

The FlapTaxTokenV3 contract is an ERC-20 token deployed as an EIP-1167 minimal clone. Its ownership has been renounced, meaning no external entity can call owner-restricted functions. No critical or high-severity vulnerabilities were identified during this audit.

> **Final Recommendation:** The FlapTaxTokenV3 contract exhibits a robust security posture, primarily due to its immutable nature as an EIP-1167 minimal clone and the renunciation of its ownership. Token holders should be aware that the contract's parameters, including its tax and anti-farmer mechanisms, are permanently fixed and cannot be altered. No further actions are required regarding access control or upgradeability, as these vectors have been effectively mitigated by the deployment strategy and ownership renunciation.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The FlapTaxTokenV3 contract is an ERC-20 token implemented as an EIP-1167 minimal clone, ensuring its logic is fixed and immutable (7.1 Architecture). The contract correctly implements standard… |
| **Governance / Economics** | 9/10 | Low | The economic model of the FlapTaxTokenV3 involves a `poolState` variable that can influence transfer amounts and fees. Functions like `startMigration()` and `finalizeMigration()` are designed to… |
| **Upgrades** | 9/10 | Low | The FlapTaxTokenV3 contract is deployed as an EIP-1167 minimal clone (7.7 Upgrades). This pattern fixes the implementation bytecode at deployment, meaning the contract's logic cannot be upgraded or… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | 35.4% |
| **Top-3 Unlocked** | 70.8% |

## Security Findings

_🟡 1 Medium · ⚪ 6 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 98.7% is held, unlocked, by 10 address(es) other than the owner/deployer. No single one holds a majority: their exits thin the market rather than hand anyone the pool. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them. This assessment covers the main pool, which holds 86% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint/owner authority, mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 17.1% of supply. What remains: 7.4% in wallets, 9.8% in other contracts. 4,881 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

4,881 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $216K (DexScreener, all pools). 24h trading volume $1.9M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: 0% on buy, 0.99% on sell. Market: $216K of DEX liquidity across 2 pools. Launch: 6 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 6 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 6 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x1392...7777`](https://bscscan.com/address/0x13920fe6467e9e3c852b8d365a036c995f0f7777) |
| **Network** | BNB Chain |
| **Price** | $0.001937 |
| **24h Volume** | $1.57M |
| **Liquidity** | $184.9K |
| **Volume / Liquidity** | 8.5× |
| **Token Age** | 6d |
| **Top-10 Holders** | 17.1% of supply |
| **Buy / Sell Tax** | 0.0% / 1.0% |
| **24h Transactions** | 4795 buys / 3277 sells |

## Security Flags (4/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not Upgradeable | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not Upgradeable | ✅ | Minimal proxy clone — the implementation is fixed in its bytecode and cannot be swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0xfd55be774ea18067bd06a6aed49fb1cc4ad966e9)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/green-morning-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-06*
