---
token: LOL World Championship
ticker: 英雄联盟
network: bsc
risk_score: 0
status: low
date: 2026-10-21
---

# LOL World Championship (英雄联盟) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 0/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/lol-world-championship-bsc)

---

## Audit Summary

The FlapTaxTokenV3 is an EIP-1167 minimal clone token. Ownership has been renounced on-chain, rendering all privileged administrative functions permanently dormant. The contract logic is immutable and cannot be upgraded or altered by any party. No security vulnerabilities were identified in the provided code map.

> **Final Recommendation:** The contract is in a secure, immutable state. No further action is required for security maintenance as the administrative functions are permanently disabled. Users should continue to monitor the token's market behavior as the economic parameters are fixed.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The architecture utilizes a standard EIP-1167 minimal clone pattern, ensuring gas-efficient deployment. 7.1 Architecture is robust due to the immutable nature of the clone. 7.2 Code Security is high… |
| **Governance / Economics** | 10/10 | Low | 7.4 Economic and 7.5 Governance risks are effectively nullified by the renouncement of ownership. No external parties can influence the pool state or tax parameters. The economic model is locked in… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not possible for this deployment. The EIP-1167 clone pattern points to a fixed implementation address that cannot be modified. This eliminates risks associated with malicious logic… |

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

The ten largest holders own 41.7% of supply. Of that, 22.5% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 9.6% in wallets, 9.6% in other contracts. 388 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

388 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them. This assessment covers the main pool, which holds 38% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $58K (DexScreener, all pools). 24h trading volume $36K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: 3% on buy, 3.44% on sell. Market: $58K of DEX liquidity across 5 pools. Launch: 4 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 4 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 4 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x25e3...7777`](https://bscscan.com/address/0x25e3fe8c2bea75768591f63d26c7530690057777) |
| **Network** | BNB Chain |
| **Price** | $0.00004866 |
| **24h Volume** | $32.7K |
| **Liquidity** | $22.3K |
| **Volume / Liquidity** | 1.5× |
| **Token Age** | 4d |
| **Top-10 Holders** | 41.7% of supply |
| **Buy / Sell Tax** | 3.0% / 3.4% |
| **24h Transactions** | 321 buys / 182 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xba9a93c357c2fd6d2b3d93e8a055a20cc3a915f6)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/lol-world-championship-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-21*
