---
token: FIST
ticker: FIST
network: bsc
risk_score: 41
status: medium
date: 2026-10-25
---

# FIST (FIST) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 41/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/fist-bsc)

---

## Audit Summary

The FlapTaxTokenV3 is a minimal clone (EIP-1167) implementation of an ERC-20 token with tax-enforced transfer logic. The contract ownership has been renounced on-chain, rendering all privileged administrative functions (such as migration control) permanently dormant. The architecture is immutable, and the core token logic follows standard OpenZeppelin patterns.

> **Final Recommendation:** The protocol is in a secure, immutable state due to the renouncement of ownership. No further action is required for the current implementation. Users should be aware that the tax and migration parameters are permanently fixed and cannot be adjusted by any party.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes standard ERC-20 and EIP-712 implementations, ensuring robust compatibility with DeFi protocols. 7.1 Architecture: The EIP-1167 clone pattern ensures a lightweight and immutable… |
| **Governance / Economics** | 6/10 | Medium | 7.4 Economic: The token employs a tax-enforced mechanism that is now fixed due to ownership renouncement. 7.5 Governance: No governance mechanisms exist; the protocol is fully decentralized by the… |
| **Upgrades** | 8/10 | Low | 7.7 Upgrades: The contract is a minimal clone, meaning the logic is immutable and cannot be upgraded. 7.8 Operations: Operational risk is minimal as the contract state is locked. No further changes… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | 88.9% |
| **LP Locked** | 88.9% — Null Address |

## Security Findings

_🟡 1 Medium · ⚪ 6 Informational_

### `QA-LIQUIDITY` — Liquidity only partly locked or burned  *(Severity: Medium · Status: Acknowledged)*

88.9% of the pool's LP is burned or time-locked. 88.9% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone. 11.1% is held, unlocked, by 1 address(es) other than the owner/deployer. No single one holds a majority: their exits thin the market rather than hand anyone the pool. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them. This assessment covers the main pool, which holds 80% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint/owner authority, mint capability, LP lock/burn state, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 42.3% of supply. Of that, 4.3% burned, 26.8% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 5.3% in wallets, 6.0% in other contracts. 2,255 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

2,255 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $33K (DexScreener, all pools). 24h trading volume $327K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: 1% on buy, 1% on sell. Market: $33K of DEX liquidity across 7 pools. Launch: 1 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 1 day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 1 day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xb19c...7777`](https://bscscan.com/address/0xb19c9a36bda28ebb340dbe3a11d3cff9cab87777) |
| **Network** | BNB Chain |
| **Price** | $0.00005542 |
| **24h Volume** | $279.1K |
| **Liquidity** | $26.4K |
| **Volume / Liquidity** | 10.6× |
| **Token Age** | 1d |
| **Top-10 Holders** | 42.3% of supply |
| **Buy / Sell Tax** | 1.0% / 1.0% |
| **24h Transactions** | 3303 buys / 2207 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x9f344a29d02867b7b4a33bb309c6d4594600f191)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/fist-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-25*
