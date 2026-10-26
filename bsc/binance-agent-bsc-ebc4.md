---
token: Binance Agent
ticker: 7AGENT
network: bsc
risk_score: 2
status: low
date: 2026-10-26
---

# Binance Agent (7AGENT) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 2/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/binance-agent-bsc-ebc4)

---

## Audit Summary

The FlapTaxTokenV3 is a minimal clone (EIP-1167) implementation of an ERC-20 token with custom tax and migration logic. Ownership has been renounced on-chain, rendering the privileged migration functions dormant and immutable. The contract architecture is standard for upgradeable-style clones, though the implementation itself is fixed and cannot be modified.

> **Final Recommendation:** The contract is secure due to the renouncement of ownership, which prevents any further administrative changes to the migration state or tax logic. No further action is required as the contract is immutable and the logic is well-contained.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The contract utilizes a robust EIP-1167 minimal clone pattern, ensuring consistent logic deployment. 7.1 Architecture is sound, utilizing standard OpenZeppelin upgradeable base contracts. 7.2 Code… |
| **Governance / Economics** | 10/10 | Low | 7.4 Economic parameters are fixed due to the renounced ownership. 7.5 Governance is effectively non-existent as no administrative actions can be performed. The tokenomics rely on the immutable state… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are impossible for this contract as it is a minimal clone with a fixed implementation address. 7.8 Operations are stable because the logic cannot be altered post-deployment. The contract… |

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

The ten largest holders own 15.1% of supply. Of that, 0.3% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 14.0% in wallets, 0.7% in other contracts. 2,936 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

2,936 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $1.3M (DexScreener, all pools). 24h trading volume $3.7M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: 0% on buy, 1% on sell. Market: $1.3M of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x2ef0...7777`](https://bscscan.com/address/0x2ef0116d3e2d0091c898ac0b09d780d5e7a17777) |
| **Network** | BNB Chain |
| **Price** | $0.1942 |
| **24h Volume** | $3.74M |
| **Liquidity** | $1.27M |
| **Volume / Liquidity** | 3.0× |
| **Token Age** | 1h |
| **Top-10 Holders** | 15.1% of supply |
| **Buy / Sell Tax** | 0.0% / 1.0% |
| **24h Transactions** | 10731 buys / 1253 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x0ae8a936a65968545552cbe7835db4d4ae2925cc)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/binance-agent-bsc-ebc4)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-26*
