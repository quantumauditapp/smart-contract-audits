---
token: PoolLuanch新币侦测
ticker: SLIME
network: bsc
risk_score: 16
status: low
date: 2026-11-06
---

# PoolLuanch新币侦测 (SLIME) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 16/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/poolluanch-bsc)

---

## Audit Summary

The FlapTaxTokenV3 is a standard ERC-20 token implemented as an EIP-1167 minimal clone. The contract ownership has been renounced, effectively locking the administrative functions that control migration states and tax parameters. The architecture is immutable, and the code follows standard OpenZeppelin patterns for upgradeable contracts, though the clone pattern ensures no further logic changes are possible.

> **Final Recommendation:** The protocol is in a secure, immutable state due to the renunciation of ownership. No further administrative actions are possible, which protects users from centralized risk. 

Users should verify the contract address against official documentation to ensure they are interacting with the intended clone. No further security interventions are required as the contract logic is locked.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The architecture utilizes a robust EIP-1167 minimal clone pattern, ensuring consistent logic across deployments. Code security is high, leveraging audited OpenZeppelin libraries for ERC-20 and permit… |
| **Governance / Economics** | 9/10 | Low | Governance is effectively decentralized through the renunciation of ownership, preventing any further manipulation of token tax states or migration parameters. 7.3 Access Control is now permanently… |
| **Upgrades** | 10/10 | Low | The contract is an immutable minimal clone, meaning 7.7 Upgrades are impossible. This eliminates the risk of malicious logic updates or proxy-based rug pulls. 7.8 Operations are stable as the… |

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

The ten largest holders own 37.8% of supply. Of that, 6.6% locked, 17.6% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 11.6% in wallets, 2.0% in other contracts. 416 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

416 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $28K (DexScreener, all pools). 24h trading volume $138K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: 1% on buy, 1% on sell. Market: $28K of DEX liquidity across 1 pools. Launch: 2 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 2 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 2 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x8351...7777`](https://bscscan.com/address/0x8351311fe78e9045a5eebcb11db9d700658c7777) |
| **Network** | BNB Chain |
| **Price** | $0.00007856 |
| **24h Volume** | $138.0K |
| **Liquidity** | $27.6K |
| **Volume / Liquidity** | 5.0× |
| **Token Age** | 2d |
| **Top-10 Holders** | 37.8% of supply |
| **Buy / Sell Tax** | 1.0% / 1.0% |
| **24h Transactions** | 1251 buys / 819 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x5d506893c5a4f44263b451b9a1065888ea07740c)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/poolluanch-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-06*
