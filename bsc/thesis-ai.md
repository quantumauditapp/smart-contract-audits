---
token: Thesis AI
ticker: THESIS
network: bsc
risk_score: 0
status: low
date: 2026-10-01
---

# Thesis AI (THESIS) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 0/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/thesis-ai-bsc)

---

## Audit Summary

The FlapTaxTokenV3 contract is an ERC-20 token deployed as an EIP-1167 minimal clone, ensuring its logic is immutable. Ownership of the contract has been renounced, effectively disabling all owner-restricted functions such as `startMigration` and `finalizeMigration`. This significantly reduces central point of failure risks. No critical or high-severity vulnerabilities were identified during the audit.

> **Final Recommendation:** Given the renounced ownership and immutable nature of the contract, the primary recommendations focus on ongoing monitoring. Users should verify the contract's interactions with any external protocols. Ensure all integrations correctly account for the token's fixed logic and the absence of administrative control.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The FlapTaxTokenV3 contract implements the ERC-20 standard and is deployed as an EIP-1167 minimal clone, ensuring its bytecode and logic are fixed. The contract includes a `poolState` variable that… |
| **Governance / Economics** | 10/10 | Low | Governance and economic risks are significantly mitigated as the contract's ownership has been renounced on-chain. This action renders all `onlyOwner` functions, including `transferOwnership`… |
| **Upgrades** | 10/10 | Low | The FlapTaxTokenV3 contract is deployed as an EIP-1167 minimal clone, which means its implementation is fixed at deployment and cannot be upgraded or altered (7.7 Upgrades). This design choice… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 99.9% (≈ permanent lock) |
| **LP Locked** | 99.9% — Null Address |

## Security Findings

_⚪ 7 Informational_

### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint/owner authority, mint capability, LP lock/burn state, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 17.4% of supply. Of that, 6.8% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 2.2% in wallets, 8.4% in other contracts. The deployer/owner wallet itself holds 1.0%. 2,706 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Thesis AI (THESIS), rank #3445. 2,706 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

99.9% of the pool's LP is burned or time-locked. 99.9% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone. 0.1% is held, unlocked, by 1 address(es) other than the owner/deployer. No single one holds a majority: their exits thin the market rather than hand anyone the pool. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $78K (DexScreener, all pools). 24h trading volume $554K (CoinGecko, all markets, daily snapshot). 24h trading volume $546K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $78K of DEX liquidity across 2 pools. Launch: 1 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 1 day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 1 day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x4519...7777`](https://bscscan.com/address/0x4519cacc591aecc5f8476bebee43b11ffedd7777) |
| **Network** | BNB Chain |
| **Price** | $0.0005644 |
| **24h Volume** | $546.2K |
| **Liquidity** | $78.4K |
| **Volume / Liquidity** | 7.0× |
| **Token Age** | 1d |
| **Top-10 Holders** | 17.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2271 buys / 2784 sells |

## Security Flags (5/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ✅ Pass |
| Not Upgradeable | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not Upgradeable | ✅ | Minimal proxy clone — the implementation is fixed in its bytecode and cannot be swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0xc0b877452f889983b9d69dd8dd2cb08561e901ea)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/thesis-ai-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-01*
