---
token: BNC Standard Corporation
ticker: BNC纳斯达克
network: bsc
risk_score: 25
status: low
date: 2026-10-26
---

# BNC Standard Corporation (BNC纳斯达克) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 25/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/bnc-standard-corporation-bsc)

---

## Audit Summary

The FlapTaxTokenV3 is an EIP-1167 minimal clone token. The ownership has been renounced on-chain, rendering all privileged administrative functions permanently inaccessible. The contract logic is immutable and functions as a standard ERC-20 token with specific tax and migration states that are now locked in their current configuration.

> **Final Recommendation:** No security issues were identified. The contract is in a permanent, immutable state due to the renunciation of ownership. Users can interact with the token with the assurance that the contract logic cannot be modified by any party.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The architecture utilizes a secure EIP-1167 minimal clone pattern, ensuring gas-efficient deployment. 7.1 Architecture is robust, and 7.2 Code Security is high due to the use of standard OpenZeppelin… |
| **Governance / Economics** | 6/10 | Medium | 7.4 Economic and 7.5 Governance risks are effectively mitigated by the renunciation of ownership. No external entity can alter the poolState or tax parameters, providing certainty to token holders.… |
| **Upgrades** | 9/10 | Low | 7.7 Upgrades are not applicable as this is an EIP-1167 minimal clone, which is inherently immutable. The implementation address is fixed at deployment. 7.8 Operations are stable, as no further… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 1 Medium · ⚪ 6 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a wallet, 0x14e5…be4a — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint/owner authority, mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 47.2% of supply. Of that, 7.9% burned — not holders that can sell, so excluded from the concentration score. What remains: 7.3% in wallets, 32.0% in other contracts. 21,968 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

21,968 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $13K (DexScreener, all pools). 24h trading volume $138K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: 3% on buy, 2.97% on sell. Market: $13K of DEX liquidity across 3 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xe780...7777`](https://bscscan.com/address/0xe78083b53f1d17b6d782106ce865c187fbb57777) |
| **Network** | BNB Chain |
| **Price** | $0.00002013 |
| **24h Volume** | $65.7K |
| **Liquidity** | $13.5K |
| **Volume / Liquidity** | 4.9× |
| **Token Age** | 10h |
| **Top-10 Holders** | 47.2% of supply |
| **Buy / Sell Tax** | 3.0% / 3.0% |
| **24h Transactions** | 5611 buys / 672 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x626338ca534b6171fcb5b7281a0a67418e331906)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/bnc-standard-corporation-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-26*
