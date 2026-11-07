---
token: XiaomiS7
ticker: XIAOMIS7
network: bsc
risk_score: 0
status: low
date: 2026-11-07
---

# XiaomiS7 (XIAOMIS7) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 0/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/xiaomis7-bsc)

---

## Audit Summary

The FlapTaxTokenV3 is a minimal clone (EIP-1167) implementation of an ERC-20 token with custom tax and migration logic. The contract ownership has been renounced on-chain, effectively disabling all privileged administrative functions. The codebase follows standard OpenZeppelin patterns for upgradeable contracts, though the deployment method renders the implementation immutable.

> **Final Recommendation:** The contract is in a secure, immutable state due to the renounced ownership. No further administrative actions are possible, which eliminates risks associated with centralized control or malicious migration triggers. Users should treat the token as a standard, non-upgradeable ERC-20 asset.

Monitor the token for any unexpected behavior in the tax-enforced state, though the logic is fixed and cannot be altered by any party. No further security interventions are required.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The architecture utilizes EIP-1167 minimal clones to ensure gas-efficient deployment. Code security is robust, leveraging well-audited OpenZeppelin libraries for ERC-20 and EIP-712 compliance. 7.1… |
| **Governance / Economics** | 10/10 | Low | The economic model is fixed due to the renounced ownership status. 7.4 Economic: Migration logic is now dormant. 7.5 Governance: No active governance or administrative control exists. 7.8 Operations… |
| **Upgrades** | 10/10 | Low | The contract is deployed as a minimal clone, which is inherently immutable. 7.7 Upgrades: No upgrade path exists for the implementation logic. The use of Initializable base contracts is appropriate… |

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

The ten largest holders own 26.5% of supply. Of that, 11.2% burned, 7.7% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 6.2% in wallets, 1.4% in other contracts. The deployer/owner wallet itself holds 4.5%. 1,451 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

1,451 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

99.9% of the pool's LP is burned or time-locked. 99.9% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $63K (DexScreener, all pools). 24h trading volume $618K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: 2% on buy, 2% on sell. Market: $63K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x2567...7777`](https://bscscan.com/address/0x2567e74882c92ded24f7df2767184af19b1b7777) |
| **Network** | BNB Chain |
| **Price** | $0.000422 |
| **24h Volume** | $617.5K |
| **Liquidity** | $62.6K |
| **Volume / Liquidity** | 9.9× |
| **Token Age** | 4h |
| **Top-10 Holders** | 26.5% of supply |
| **Buy / Sell Tax** | 2.0% / 2.0% |
| **24h Transactions** | 3523 buys / 1410 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x507f990196168571adc3cfac23d860da6fdd13f9)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/xiaomis7-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-07*
