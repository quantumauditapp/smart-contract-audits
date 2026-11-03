---
token: BUILD N BUILD
ticker: 共建
network: bsc
risk_score: 22
status: low
date: 2026-11-03
---

# BUILD N BUILD (共建) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 22/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/build-n-build-bsc)

---

## Audit Summary

The FlapTaxTokenV3 is a minimal clone (EIP-1167) implementing a tax-enforced token model. The contract ownership has been renounced on-chain, effectively disabling all privileged administrative functions. The architecture is immutable, and the token logic is locked to the current implementation.

> **Final Recommendation:** The contract is in a secure, immutable state with no active administrative risks. Users should be aware that the tax and migration logic is permanently fixed and cannot be adjusted by any party. No further security actions are required.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The contract utilizes standard OpenZeppelin libraries for ERC-20 and EIP-712 functionality, ensuring robust base security. 7.1 Architecture is based on a secure EIP-1167 minimal clone pattern, while… |
| **Governance / Economics** | 6/10 | Medium | 7.4 Economic parameters are fixed by the immutable state of the contract. 7.5 Governance is non-existent as the owner has renounced control, preventing any further changes to the tax or migration… |
| **Upgrades** | 9/10 | Low | 7.7 Upgrades are impossible for this contract as it is deployed as an EIP-1167 minimal clone. The implementation address is hardcoded into the proxy bytecode, ensuring the logic cannot be swapped.… |

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

The ten largest holders own 19.7% of supply. Of that, 0.5% burned — not holders that can sell, so excluded from the concentration score. What remains: 4.1% in wallets, 15.2% in other contracts. 26,147 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

26,147 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $48K (DexScreener, all pools). 24h trading volume $219K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: 3% on buy, 2.97% on sell. Market: $48K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x2675...7777`](https://bscscan.com/address/0x26752e97156af5be25e16b43fa91fb24adaf7777) |
| **Network** | BNB Chain |
| **Price** | $0.000283 |
| **24h Volume** | $218.6K |
| **Liquidity** | $48.0K |
| **Volume / Liquidity** | 4.6× |
| **Token Age** | 9h |
| **Top-10 Holders** | 19.7% of supply |
| **Buy / Sell Tax** | 3.0% / 3.0% |
| **24h Transactions** | 7524 buys / 1058 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x847d559d8e3efad25bca534942da430ee1ce632c)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/build-n-build-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-03*
