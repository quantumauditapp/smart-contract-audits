---
token: one life, its worth an attempt
ticker: WORTH
network: base
risk_score: 84
status: high
date: 2026-10-24
---

# one life, its worth an attempt (WORTH) — Smart Contract Security Analysis | Base

> **Risk Score: 84/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/one-life-its-worth-an-attempt-base-36a3)

---

## Audit Summary

The contract at the provided address is not verified on the Base block explorer. As the source code is unavailable, it is impossible to perform a technical security audit. Investors should exercise extreme caution as unverified contracts may contain malicious functions such as honeypot mechanisms, hidden minting capabilities, or blacklists.

> **Final Recommendation:** Do not interact with this contract. Without verified source code, there is no assurance that the contract functions as intended or that funds are secure. Users should avoid providing liquidity or purchasing tokens associated with unverified addresses.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | 7.1 Architecture: Unknown. 7.2 Code Security: Cannot be verified due to lack of source code. 7.3 Access Control: Cannot be verified. 7.6 External: Unknown dependencies. |
| **Governance / Economics** | 1/10 | High | 7.4 Economic: Tokenomics and supply mechanics are opaque. 7.5 Governance: No insight into ownership or administrative privileges. 7.8 Operations: High risk of rug-pull or malicious tax implementation. |
| **Upgrades** | 5/10 | Medium | 7.7 Upgrades: Cannot determine if the contract is immutable or utilizes a proxy pattern. Without source code, any potential upgradeability remains a hidden risk. |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🔴 1 Critical · 🟠 1 High · ⚪ 5 Informational_

### `C-01` — Unverified Source Code  *(Severity: Critical · Status: Unresolved)*

The contract source code is not published on the block explorer. This prevents any security analysis and hides potential malicious logic.

**Recommendation:** Verify the contract source code on the block explorer to allow for transparency and community review.


### `QA-LIQUIDITY` — Liquidity withdrawable by the owner/deployer  *(Severity: High · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by the token's owner/deployer (0x2ea3…e2d5) — they can pull that liquidity at any moment. This is the rug-pull path. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 39.4% of supply. What remains: 25.1% in wallets, 14.3% in other contracts. 923 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

923 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $141K (DexScreener, all pools). 24h trading volume $1.3M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mint capability could not be read. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $141K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x77d1...2994`](https://basescan.org/address/0x77d166a269f544cc2cb5006f3a38dafffb752994) |
| **Network** | Base |
| **Price** | $0.00000534 |
| **24h Volume** | $1.34M |
| **Liquidity** | $140.7K |
| **Volume / Liquidity** | 9.5× |
| **Token Age** | 4h |
| **Top-10 Holders** | 39.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1847 buys / 1260 sells |

## Security Flags (1/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ❌ Fail |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ⚠️ Unknown |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ❌ | Source code is **not verified** — contract logic is opaque. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/base/0xd6edb2b9708d20d706e1cc8418766a15c6781b1755b6093483ca8b4abb877876)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/one-life-its-worth-an-attempt-base-36a3)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-24*
