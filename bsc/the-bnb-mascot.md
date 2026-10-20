---
token: The BNB Mascot
ticker: BUILDER
network: bsc
risk_score: 0
status: low
date: 2026-10-08
---

# The BNB Mascot (BUILDER) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 0/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/the-bnb-mascot-bsc)

---

## Audit Summary

The FlapTaxTokenV3 contract is an ERC-20 token deployed as an EIP-1167 minimal clone, meaning its logic is immutable. Ownership has been renounced, effectively disabling all owner-restricted functions, including those that could modify the token's tax and anti-farmer mechanisms. No critical or high-severity vulnerabilities were identified.

> **Final Recommendation:** Given that ownership has been renounced and the contract is a minimal clone, its behavior is immutable and no longer subject to administrative control. Users should be aware that the token's tax and anti-farmer mechanisms are fixed and cannot be altered. Future interactions should account for these static parameters.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The FlapTaxTokenV3 contract implements the ERC-20 standard, providing standard token functionalities such as `transfer` and `balanceOf`. It is deployed as an EIP-1167 minimal clone, ensuring its… |
| **Governance / Economics** | 10/10 | Low | The contract incorporates economic mechanisms related to `poolState`, which dictate transfer amounts and fees, including tax and anti-farmer features (7.4 Economic). These mechanisms were designed to… |
| **Upgrades** | 10/10 | Low | The FlapTaxTokenV3 contract is deployed as an EIP-1167 minimal clone, which means its implementation is fixed and cannot be upgraded or modified after deployment (7.7 Upgrades). While it inherits… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Null Address |

## Security Findings

_⚪ 6 Informational_

### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint/owner authority, mint capability, LP lock/burn state, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 34.3% of supply. Of that, 7.8% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 13.7% in wallets, 12.7% in other contracts. 534 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

534 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $72K (DexScreener, all pools). 24h trading volume $156K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $72K of DEX liquidity across 1 pools. Launch: 30 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x1b94...7777`](https://bscscan.com/address/0x1b947cb610f3b39b3148b33e8eceded2d7997777) |
| **Network** | BNB Chain |
| **Price** | $0.0004427 |
| **24h Volume** | $156.5K |
| **Liquidity** | $71.8K |
| **Volume / Liquidity** | 2.2× |
| **Token Age** | 1mo |
| **Top-10 Holders** | 34.3% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 368 buys / 362 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x4686368fdea0cdcfa07aec749fddada9b2c5ed95)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/the-bnb-mascot-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-08*
