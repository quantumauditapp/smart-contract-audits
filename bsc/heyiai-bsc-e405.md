---
token: heyi.ai
ticker: HEYI
network: bsc
risk_score: 21
status: low
date: 2026-10-23
---

# heyi.ai (HEYI) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 21/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/heyiai-bsc-e405)

---

## Audit Summary

The FlapTaxTokenV3 is a minimal clone (EIP-1167) implementation of an ERC-20 token with migration-based tax logic. The contract ownership has been renounced on-chain, effectively locking the privileged migration functions and ensuring the current state is immutable. The architecture is standard for upgradeable-style tokens, though the deployment pattern prevents future logic changes.

> **Final Recommendation:** The protocol is in a secure, immutable state due to the renunciation of ownership. No further action is required for the current deployment. Users should verify the contract address against official documentation to ensure they are interacting with the intended immutable instance.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The contract utilizes a robust EIP-1167 minimal clone pattern, ensuring consistent logic across instances. 7.1 Architecture is sound, relying on standard OpenZeppelin libraries for ERC-20 and permit… |
| **Governance / Economics** | 7/10 | Low | 7.4 Economic and 7.5 Governance risks are mitigated by the renunciation of ownership. Since the owner can no longer trigger startMigration or finalizeMigration, the token's tax and anti-farmer logic… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable as the contract is a minimal clone, which is inherently immutable. The implementation address is hardcoded into the proxy bytecode, preventing any future logic… |

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

The ten largest holders own 58.1% of supply. Of that, 43.9% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 8.2% in wallets, 6.0% in other contracts. 365 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

365 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $12K (DexScreener, all pools). 24h trading volume $1.0M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: 1% on buy, 1% on sell. Market: $12K of DEX liquidity across 2 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x7832...7777`](https://bscscan.com/address/0x7832c85c1910945d54494424f606e90c92cf7777) |
| **Network** | BNB Chain |
| **Price** | $0.00001309 |
| **24h Volume** | $1.01M |
| **Liquidity** | $11.6K |
| **Volume / Liquidity** | 86.5× |
| **Token Age** | 7h |
| **Top-10 Holders** | 58.1% of supply |
| **Buy / Sell Tax** | 1.0% / 1.0% |
| **24h Transactions** | 5078 buys / 3843 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x6e43f2662b9ee9065a0ca951552589b5a5313dbf)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/heyiai-bsc-e405)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-23*
