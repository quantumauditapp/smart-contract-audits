---
token: CiShanGou_GiggleAcademy
ticker: 慈善狗
network: bsc
risk_score: 9
status: low
date: 2026-10-23
---

# CiShanGou_GiggleAcademy (慈善狗) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 9/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/cishangougiggleacademy-bsc)

---

## Audit Summary

The FlapTaxTokenV3 is a minimal clone implementation of an ERC-20 token with built-in migration logic. The contract ownership has been renounced, rendering the migration functions dormant and effectively locking the current pool state. The architecture is standard for EIP-1167 clones, and no critical vulnerabilities were identified in the provided code map.

> **Final Recommendation:** The protocol is in a secure, immutable state due to the renunciation of ownership. No further action is required for the current deployment as the privileged functions are permanently disabled.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The contract utilizes a robust EIP-1167 minimal clone pattern, ensuring consistent logic deployment. 7.1 Architecture is sound, utilizing standard OpenZeppelin upgradeable libraries for ERC-20… |
| **Governance / Economics** | 7/10 | Low | 7.4 Economic and 7.5 Governance risks are effectively mitigated by the renunciation of ownership. Since the owner cannot trigger migration functions, the token's economic parameters are immutable.… |
| **Upgrades** | 9/10 | Low | 7.7 Upgrades are not applicable as this is an EIP-1167 minimal clone. The implementation address is immutable, preventing any future logic updates. This design choice provides high security by… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 89.3% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 1 Medium · ⚪ 6 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 3 address(es) other than the owner/deployer. One of them — a wallet, 0xda0a…6ec1 — holds 89.3% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint/owner authority, mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 19.7% of supply. Of that, 1.7% burned — not holders that can sell, so excluded from the concentration score. What remains: 5.2% in wallets, 12.8% in other contracts. 1,661 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

1,661 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $53K (DexScreener, all pools). 24h trading volume $537K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: 3% on buy, 2.97% on sell. Market: $53K of DEX liquidity across 2 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x526a...7777`](https://bscscan.com/address/0x526a0713a85dd82fea9ea1e60c2fb6da27407777) |
| **Network** | BNB Chain |
| **Price** | $0.0003059 |
| **24h Volume** | $462.6K |
| **Liquidity** | $53.5K |
| **Volume / Liquidity** | 8.6× |
| **Token Age** | 7h |
| **Top-10 Holders** | 19.7% of supply |
| **Buy / Sell Tax** | 3.0% / 3.0% |
| **24h Transactions** | 4559 buys / 2907 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x1ac61ff9dcfe4ff14370244a90269c1220f29d6a)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/cishangougiggleacademy-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-23*
