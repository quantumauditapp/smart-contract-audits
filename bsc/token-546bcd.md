---
token: 雪球
ticker: 雪球
network: bsc
risk_score: 29
status: low
date: 2026-11-04
---

# 雪球 (雪球) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 29/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/token-546bcd-bsc)

---

## Audit Summary

AgentToken is a standard ERC-20 implementation with a restricted configuration mechanism for liquidity pair management. The contract utilizes OpenZeppelin standards and includes a one-time setup function for the liquidity pair. No vulnerabilities were identified in the provided code map.

> **Final Recommendation:** The contract is well-structured and follows security best practices for standard tokens. Ensure the 'launch' address is a secure multi-sig wallet to prevent unauthorized configuration of the liquidity pair.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The architecture follows standard ERC-20 patterns with clean separation of concerns. 7.1 Architecture is robust, utilizing standard inheritance. 7.2 Code Security is high due to the use of modern… |
| **Governance / Economics** | 2/10 | High | 7.4 Economic and 7.5 Governance aspects are minimal as the contract is a standard token. The 'configurePair' function is restricted to a single-use setup, preventing ongoing governance manipulation.… |
| **Upgrades** | 6/10 | Medium | 7.7 Upgrades are not supported as the contract is not a proxy. 7.8 Operations are straightforward with no complex state transitions beyond the initial pair configuration. |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | 85.2% |
| **LP Locked** | 85.2% |

## Security Findings

_🟡 1 Medium · ⚪ 6 Informational_

### `QA-LIQUIDITY` — Liquidity only partly locked or burned  *(Severity: Medium · Status: Acknowledged)*

85.2% of the pool's LP is burned or time-locked. 85.2% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone. 12.7% is held, unlocked, by 9 address(es) other than the owner/deployer. No single one holds a majority: their exits thin the market rather than hand anyone the pool. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint capability, LP lock/burn state, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 35.3% of supply. Of that, 20.8% burned, 8.2% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 5.5% in wallets, 0.8% in other contracts. 461 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

461 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $13K (DexScreener, all pools). 24h trading volume $244K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: 3% on buy, 3% on sell. Market: $13K of DEX liquidity across 2 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xf88c...d98a`](https://bscscan.com/address/0xf88c76a67e349cbdaf5d4ac3e00837969231d98a) |
| **Network** | BNB Chain |
| **Price** | $77.2200 |
| **24h Volume** | $244.1K |
| **Liquidity** | $12.9K |
| **Volume / Liquidity** | 19.0× |
| **Token Age** | 19h |
| **Top-10 Holders** | 35.3% of supply |
| **Buy / Sell Tax** | 3.0% / 3.0% |
| **24h Transactions** | 3502 buys / 1949 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0xc21423493c32f9214722a430b006b262839d63b3)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/token-546bcd-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-04*
