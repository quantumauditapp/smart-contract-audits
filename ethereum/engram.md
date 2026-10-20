---
token: Engram
ticker: ENGRAM
network: ethereum
risk_score: 15
status: low
date: 2026-10-07
---

# Engram (ENGRAM) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 15/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/engram-eth)

---

## Audit Summary

The Engram contract functions as a basic token, implementing core transfer functionalities. No critical or high-severity vulnerabilities were identified during the audit. The contract exhibits a simple architecture with no complex access control or upgrade mechanisms. However, it lacks several standard ERC-20 functions, which may impact its compatibility and usability within the broader ecosystem.

> **Final Recommendation:** The Engram contract is a simple token implementation with no identified critical vulnerabilities. To enhance its robustness and ecosystem compatibility, consider implementing the full ERC-20 standard, specifically adding `totalSupply()`, `balanceOf(address)`, and `allowance(address,address)` functions. This will ensure broader integration and expected behavior for token holders.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The Engram contract (7.1 Architecture) implements basic token transfer logic via `transfer` and `transferFrom` functions, demonstrating a straightforward design. There are no privileged functions or… |
| **Governance / Economics** | 2/10 | High | The Engram contract does not incorporate any governance mechanisms (7.5 Governance) or complex economic models (7.4 Economic). This simplicity reduces the attack surface associated with intricate… |
| **Upgrades** | 8/10 | Low | The Engram contract is not designed as an upgradeable proxy (7.7 Upgrades). This eliminates all risks associated with upgrade mechanisms, such as proxy initialization errors, storage collisions, or… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 1 Medium · ⚪ 6 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a contract, 0x7ad8…3acd — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them. This assessment covers the main pool, which holds 66% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 34.7% of supply. What remains: 6.9% in wallets, 27.7% in other contracts. 344 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

344 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $114K (DexScreener, all pools). 24h trading volume $492K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $114K of DEX liquidity across 7 pools. Launch: 1 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 1 day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 1 day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x56c9...7cc6`](https://etherscan.io/address/0x56c915d92e24255fdc52eb114a31399c432b7cc6) |
| **Network** | Ethereum |
| **Price** | $0.0005843 |
| **24h Volume** | $420.6K |
| **Liquidity** | $75.5K |
| **Volume / Liquidity** | 5.6× |
| **Token Age** | 1d |
| **Top-10 Holders** | 34.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 918 buys / 713 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0xc3bcbfb2b362b046448a1c0fddfd7b12aab9d877bacb6ba26172e552af8e8c73)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/engram-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-07*
