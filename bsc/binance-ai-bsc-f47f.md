---
token: Binance AI
ticker: BIBI
network: bsc
risk_score: 33
status: low
date: 2026-10-21
---

# Binance AI (BIBI) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 33/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/binance-ai-bsc-f47f)

---

## Audit Summary

The FlapTaxTokenV3 is an EIP-1167 minimal clone implementation. Ownership has been renounced on-chain, effectively disabling all privileged administrative functions. The contract logic is immutable and secure against unauthorized state changes. Coverage: 7.1 Architecture (Minimal Clone), 7.2 Code Security (Standard), 7.3 Access Control (Renounced), 7.4 Economic (Fixed), 7.5 Governance (None), 7.6 External (Standard), 7.7 Upgrades (None), 7.8 Operations (Standard).

> **Final Recommendation:** The contract is secure and immutable. No further action is required as the ownership has been renounced, preventing any future administrative changes to the token's tax or migration state. Users can interact with the contract with confidence in its current configuration.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The contract utilizes a standard EIP-1167 minimal clone pattern, ensuring consistent logic across deployments. The codebase follows standard ERC-20 and EIP-712 specifications for permit… |
| **Governance / Economics** | 5/10 | Medium | Governance is non-existent due to the renunciation of ownership. The economic parameters are fixed and cannot be altered by any party. This provides high certainty for token holders regarding the… |
| **Upgrades** | 9/10 | Low | The contract is an EIP-1167 minimal clone, which is inherently immutable. There are no proxy upgrade mechanisms or logic pointers that can be modified. The implementation is fixed at the time of… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 1 Medium · ⚪ 6 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a wallet, 0xddac…308c — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint/owner authority, mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 53.7% of supply. What remains: 37.6% in wallets, 16.1% in other contracts. 21,545 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

21,545 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $27K (DexScreener, all pools). 24h trading volume $364K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: 2% on buy, 1.98% on sell. Market: $27K of DEX liquidity across 2 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x9baf...7777`](https://bscscan.com/address/0x9bafb44d7cc9394465a96ef0637f6cbce8e47777) |
| **Network** | BNB Chain |
| **Price** | $0.00008629 |
| **24h Volume** | $353.4K |
| **Liquidity** | $27.2K |
| **Volume / Liquidity** | 13.0× |
| **Token Age** | 17h |
| **Top-10 Holders** | 53.7% of supply |
| **Buy / Sell Tax** | 2.0% / 2.0% |
| **24h Transactions** | 3935 buys / 1998 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x38dd732f1201212d0caa22e3586d0a18b07ba940)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/binance-ai-bsc-f47f)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-21*
