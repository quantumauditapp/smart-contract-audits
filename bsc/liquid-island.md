---
token: Liquid Island
ticker: ISLAND
network: bsc
risk_score: 16
status: low
date: 2026-11-07
---

# Liquid Island (ISLAND) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 16/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/liquid-island-bsc)

---

## Audit Summary

The FlapTaxTokenV3 is a minimal clone (EIP-1167) implementation of an ERC-20 token with custom tax and migration logic. The contract ownership has been renounced, effectively locking the administrative functions startMigration and finalizeMigration. The architecture is immutable, and the code follows standard OpenZeppelin patterns for token functionality.

> **Final Recommendation:** The contract is in a locked, immutable state due to the renunciation of ownership. No further administrative actions are required or possible. Users should be aware that the current tax and migration parameters are permanent and cannot be adjusted by any party.

Given the immutability, the protocol is highly resistant to administrative rug-pulls or unauthorized logic changes. Ensure that the current state of the pool parameters meets the long-term requirements of the token ecosystem, as no future updates can be applied.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The contract utilizes a standard EIP-1167 minimal clone pattern, ensuring consistent logic across deployments. 7.1 Architecture is robust and immutable, while 7.2 Code Security is maintained through… |
| **Governance / Economics** | 9/10 | Low | 7.4 Economic parameters are currently fixed due to the renounced ownership, preventing any further manipulation of tax or migration states. 7.5 Governance is non-existent as the contract is now fully… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable as the contract is a minimal clone with fixed bytecode. The implementation address is hardcoded and cannot be modified. 7.8 Operations are stable, as the contract… |

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

The ten largest holders own 65.3% of supply. Of that, 8.8% locked, 42.1% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 5.7% in wallets, 8.6% in other contracts. 333 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

333 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $11K (DexScreener, all pools). 24h trading volume $172K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: 2% on buy, 2.18% on sell. Market: $11K of DEX liquidity across 2 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x28ef...7777`](https://bscscan.com/address/0x28ef2256fe6fbdcb1f0f2dbdee0a082ff7017777) |
| **Network** | BNB Chain |
| **Price** | $0.00001219 |
| **24h Volume** | $95.4K |
| **Liquidity** | $10.5K |
| **Volume / Liquidity** | 9.1× |
| **Token Age** | 4h |
| **Top-10 Holders** | 65.3% of supply |
| **Buy / Sell Tax** | 2.0% / 2.2% |
| **24h Transactions** | 1279 buys / 1123 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xe1d2a9e062093645a867fc2aa2072850af090e74)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/liquid-island-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-07*
