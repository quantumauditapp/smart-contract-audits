---
token: Ye Hi
ticker: YEHI
network: bsc
risk_score: 26
status: low
date: 2026-10-08
---

# Ye Hi (YEHI) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 26/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/ye-hi-bsc)

---

## Audit Summary

The BrewToken contract is a standard ERC-20 token implementation. The audit found no critical, high, medium, or low severity vulnerabilities. The contract adheres closely to the ERC-20 standard without additional complex logic or privileged functions, contributing to its low-risk profile.

> **Final Recommendation:** Given the contract's simplicity as a standard ERC-20 token with no custom logic or privileged functions, the primary recommendation is to ensure thorough testing of all standard ERC-20 functionalities. Additionally, users should be educated on the immutable nature of the contract and the absence of any administrative control over token behavior. For any future integrations, verify that the integrating systems correctly handle standard ERC-20 events and function calls.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The BrewToken contract implements the ERC-20 standard, including `totalSupply()`, `balanceOf()`, `transfer()`, `transferFrom()`, `approve()`, and `allowance()`. The contract does not contain any… |
| **Governance / Economics** | 1/10 | High | The BrewToken contract is a basic ERC-20 token with no special economic mechanisms or governance features (7.4 Economic, 7.5 Governance). There are no privileged roles that can alter token supply… |
| **Upgrades** | 8/10 | Low | The BrewToken contract is not implemented as a proxy and is therefore not upgradeable (7.7 Upgrades). This means its logic is immutable once deployed, eliminating risks associated with upgradeability… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 99.6% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 1 Medium · ⚪ 6 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 2 address(es) other than the owner/deployer. One of them — a contract, 0x3366…f0d4 — holds 99.6% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 44.2% of supply. Of that, 25.7% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 5.7% in wallets, 12.8% in other contracts. 450 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

450 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $42K (DexScreener, all pools). 24h trading volume $222K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $42K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xba4c...6666`](https://bscscan.com/address/0xba4c9375c899acb9b99b4a032a7756dd24ec6666) |
| **Network** | BNB Chain |
| **Price** | $0.0000923 |
| **24h Volume** | $222.2K |
| **Liquidity** | $42.4K |
| **Volume / Liquidity** | 5.2× |
| **Token Age** | 8h |
| **Top-10 Holders** | 44.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1494 buys / 820 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xda74d34ddca747500d948cc8de43517e6effeed7)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/ye-hi-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-08*
