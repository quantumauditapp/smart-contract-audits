---
token: 币安公主
ticker: 币安公主
network: bsc
risk_score: 15
status: low
date: 2026-11-05
---

# 币安公主 (币安公主) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 15/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/token-0259cd-bsc)

---

## Audit Summary

The FlapTaxTokenV3 is an ERC-20 token deployed as an EIP-1167 minimal clone. The contract ownership has been renounced on-chain, effectively disabling all privileged administrative functions. The architecture is immutable, and the token logic is standard with additional tax-enforcement states. No vulnerabilities were identified in the provided code map.

> **Final Recommendation:** The contract is in a secure, immutable state due to the renunciation of ownership. No further action is required to secure the protocol logic. Users should verify the contract address against official documentation to ensure they are interacting with the intended deployment.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The contract utilizes a standard EIP-1167 minimal clone pattern, ensuring consistent and immutable logic. 7.1 Architecture is robust due to the immutable nature of the clone. 7.2 Code Security is… |
| **Governance / Economics** | 9/10 | Low | 7.3 Access Control is effectively locked as ownership has been renounced, preventing any further administrative changes. 7.4 Economic parameters are fixed, and 7.5 Governance is non-existent due to… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are impossible for this contract because it is an EIP-1167 minimal clone, which points to a fixed implementation address. 7.8 Operations are stable, as the contract logic is immutable… |

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

The ten largest holders own 89.5% of supply. Of that, 6.9% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 1.8% in wallets, 80.8% in other contracts. 383 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

383 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $67K (DexScreener, all pools). 24h trading volume $135K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: 1% on buy, 2% on sell. Market: $67K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x0c21...7777`](https://bscscan.com/address/0x0c21248002c5bd2e96155509369508e361cd7777) |
| **Network** | BNB Chain |
| **Price** | $0.0004952 |
| **24h Volume** | $135.2K |
| **Liquidity** | $66.7K |
| **Volume / Liquidity** | 2.0× |
| **Token Age** | 10h |
| **Top-10 Holders** | 89.5% of supply |
| **Buy / Sell Tax** | 1.0% / 2.0% |
| **24h Transactions** | 1103 buys / 5369 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x30e8ad4d0064e4bd1552c129d8c032a10101d792)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/token-0259cd-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-05*
