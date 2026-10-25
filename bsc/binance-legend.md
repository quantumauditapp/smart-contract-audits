---
token: Binance Legend
ticker: 币安传奇
network: bsc
risk_score: 21
status: low
date: 2026-10-25
---

# Binance Legend (币安传奇) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 21/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/binance-legend-bsc)

---

## Audit Summary

The FlapTaxTokenV3 is an EIP-1167 minimal clone implementation of an ERC-20 token with tax and migration logic. The contract ownership has been explicitly renounced, rendering all privileged administrative functions (startMigration, finalizeMigration, transferOwnership) permanently inaccessible. The architecture is immutable, and the token functions as a standard ERC-20 with fixed logic.

> **Final Recommendation:** The contract is in a secure, immutable state due to the renouncement of ownership. No further administrative actions are possible, which eliminates the risk of rug-pulls or unauthorized state changes via privileged functions. Users should interact with the contract with the understanding that the current tax and migration logic is permanent.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The contract utilizes standard OpenZeppelin upgradeable patterns adapted for minimal clones, ensuring robust ERC-20 compliance. 7.1 Architecture is fixed via EIP-1167, preventing logic changes. 7.2… |
| **Governance / Economics** | 6/10 | Medium | 7.4 Economic and 7.5 Governance risks are minimal as the protocol has no active governance or administrative control. The token logic is immutable, preventing any future changes to tax rates or… |
| **Upgrades** | 9/10 | Low | 7.7 Upgrades are not possible for this contract due to its deployment as an EIP-1167 minimal clone. The implementation is hardcoded and cannot be modified. 7.8 Operations are stable, as the contract… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 1 Medium · ⚪ 6 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a wallet, 0x2d6c…043c — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint/owner authority, mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 34.9% of supply. Of that, 5.0% burned — not holders that can sell, so excluded from the concentration score. What remains: 10.8% in wallets, 19.1% in other contracts. 18,822 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

18,822 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $26K (DexScreener, all pools). 24h trading volume $253K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: 3% on buy, 0% on sell. Market: $26K of DEX liquidity across 2 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x9a61...7777`](https://bscscan.com/address/0x9a614cbe3936787fb7041ca6eea1b87f1a4e7777) |
| **Network** | BNB Chain |
| **Price** | $0.00007268 |
| **24h Volume** | $178.6K |
| **Liquidity** | $25.9K |
| **Volume / Liquidity** | 6.9× |
| **Token Age** | 8h |
| **Top-10 Holders** | 34.9% of supply |
| **Buy / Sell Tax** | 3.0% / 0.0% |
| **24h Transactions** | 5406 buys / 1449 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xb9cba2d721051593eafba15c5c688d1d2425a3ec)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/binance-legend-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-25*
