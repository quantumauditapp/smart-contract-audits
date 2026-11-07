---
token: Catena Labs
ticker: CTALB
network: arbitrum
risk_score: 75
status: high
date: 2026-11-07
---

# Catena Labs (CTALB) — Smart Contract Security Analysis | Arbitrum

> **Risk Score: 75/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/catena-labs-arb-4db0)

---

## Audit Summary

The contract at the provided address is not verified on the Arbitrum block explorer. Consequently, the source code is unavailable for security analysis. Investors should exercise extreme caution as the lack of transparency prevents verification of ownership, tax mechanisms, or potential backdoors.

> **Final Recommendation:** Do not interact with or provide liquidity to this contract until the source code is verified on the block explorer. Verify the contract through the standard compiler verification process to allow for a comprehensive security audit.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The technical architecture cannot be evaluated due to the absence of verified source code. 7.1 Architecture, 7.2 Code Security, 7.3 Access Control, and 7.6 External dependencies remain entirely… |
| **Governance / Economics** | 1/10 | High | Economic parameters such as 7.4 Economic and 7.5 Governance are unverifiable. There is no visibility into minting capabilities, tax logic, or ownership privileges. Investors are exposed to potential… |
| **Upgrades** | 6/10 | Medium | 7.7 Upgrades and 7.8 Operations cannot be assessed. It is unknown if the contract utilizes proxy patterns or immutable logic. The lack of verification prevents confirmation of whether the contract is… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🔴 1 Critical · 🟠 1 High · 🟡 1 Medium · ⚪ 5 Informational_

### `C-01` — Unverified Source Code  *(Severity: Critical · Status: Unresolved)*

The contract source code is not verified on the block explorer, preventing any security assessment of the logic.

**Recommendation:** Verify the contract source code on the block explorer immediately.


### `H-01` — Lack of Transparency  *(Severity: High · Status: Unresolved)*

Users cannot audit the contract for malicious functions, such as hidden minting, blacklisting, or tax manipulation.

**Recommendation:** Publish the source code and provide a clear, audited documentation of the contract's functionality.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a wallet, 0x59b0…10c2 — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 88.4% of supply. Of that, 13.3% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 75.1% in wallets, 0.0% in other contracts. The deployer/owner wallet itself holds 8.7%. 2,178 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

2,178 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $272K (DexScreener, all pools). 24h trading volume $108K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mint capability could not be read. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $272K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x43a8...33e6`](https://arbiscan.io/address/0x43a8465c709e38f4d006cc30907713337efb33e6) |
| **Network** | Arbitrum |
| **Price** | $0.01021 |
| **24h Volume** | $108.3K |
| **Liquidity** | $271.9K |
| **Volume / Liquidity** | 0.4× |
| **Token Age** | 6h |
| **Top-10 Holders** | 88.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 453 buys / 49 sells |

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

- [View on DexScreener](https://dexscreener.com/arbitrum/0x777d051f5f14d4f4f04b5b731653c144ea43d003)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/catena-labs-arb-4db0)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-07*
