---
token: WangChai
ticker: 旺柴
network: bsc
risk_score: 1
status: low
date: 2026-10-02
---

# WangChai (旺柴) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 1/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/wangchai-bsc)

---

## Audit Summary

The FlapTaxTokenV3 contract is an ERC-20 token deployed as an EIP-1167 minimal clone, ensuring its implementation is fixed and non-upgradeable. Ownership of the contract has been renounced, rendering all owner-restricted functions, including those that modify transfer fees (`poolState`), permanently inactive. This significantly reduces central control risk. No critical or high-severity vulnerabilities were identified.

> **Final Recommendation:** Users should verify the immutability of the token's logic and the renounced ownership status on-chain to confirm the absence of central control. While the contract itself appears robust due to its fixed implementation and renounced ownership, users should always exercise caution when interacting with any token and understand its specific economic model.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The FlapTaxTokenV3 contract implements standard ERC-20 functionality, ensuring basic token operations are robust (7.2 Code Security). It is deployed as an EIP-1167 minimal clone, which fixes its… |
| **Governance / Economics** | 10/10 | Low | The economic and governance risk for FlapTaxTokenV3 is significantly mitigated by the renounced ownership (7.5 Governance). This action permanently disables all functions previously restricted to the… |
| **Upgrades** | 10/10 | Low | The FlapTaxTokenV3 contract is deployed as an EIP-1167 minimal clone, meaning its implementation is fixed and cannot be upgraded or altered (7.7 Upgrades). This design choice eliminates all… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Null Address |

## Security Findings

_⚪ 7 Informational_

### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint/owner authority, mint capability, LP lock/burn state, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 18.8% of supply. Of that, 2.1% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 0.0% in wallets, 16.7% in other contracts. 4,115 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

4,115 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them. This assessment covers the main pool, which holds 80% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $430K (DexScreener, all pools). 24h trading volume $1.7M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: 1% on buy, 0.99% on sell. Market: $430K of DEX liquidity across 2 pools. Launch: 14 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 14 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 14 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x14f6...7777`](https://bscscan.com/address/0x14f6a94909c407854390aa2d2462a3095d317777) |
| **Network** | BNB Chain |
| **Price** | $0.008389 |
| **24h Volume** | $1.72M |
| **Liquidity** | $345.7K |
| **Volume / Liquidity** | 5.0× |
| **Token Age** | 14d |
| **Top-10 Holders** | 18.8% of supply |
| **Buy / Sell Tax** | 1.0% / 1.0% |
| **24h Transactions** | 8464 buys / 10776 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x223c585c50d4747653a57d577707b1eadbb2cfb0)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/wangchai-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-02*
