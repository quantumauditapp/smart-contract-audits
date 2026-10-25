---
token: Pangea
ticker: PANGEA
network: base
risk_score: 84
status: high
date: 2026-10-25
---

# Pangea (PANGEA) — Smart Contract Security Analysis | Base

> **Risk Score: 84/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/pangea-base-2a83)

---

## Audit Summary

The contract at the provided address is not verified on the Base block explorer. Consequently, the source code is unavailable for security analysis. Investors should exercise extreme caution as the lack of transparency prevents verification of ownership, tax mechanisms, or potential backdoors.

> **Final Recommendation:** Do not interact with this contract. Without verified source code, it is impossible to distinguish this token from malicious projects designed to drain user funds or restrict selling. If you are an investor, prioritize projects that provide fully verified source code on block explorers.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | 7.1 Architecture: Unknown. 7.2 Code Security: Cannot be evaluated due to lack of source code. 7.3 Access Control: Cannot be verified; potential for hidden minting or pausing functions exists. 7.6… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic: Tokenomics and tax logic are opaque. 7.5 Governance: Administrative privileges remain unknown and potentially centralized. Users have no visibility into potential honeypot mechanisms or… |
| **Upgrades** | 5/10 | Medium | 7.7 Upgrades: The contract's upgradeability status is unknown. 7.8 Operations: Operational security is compromised by the lack of public code disclosure, preventing any assessment of emergency… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🔴 1 Critical · 🟠 1 High · ⚪ 5 Informational_

### `C-01` — Unverified Contract Source Code  *(Severity: Critical · Status: Unresolved)*

The contract source code is not published on the block explorer. This prevents any security audit of the logic, including potential backdoors, minting functions, or malicious tax implementations.

**Recommendation:** Publish and verify the source code on the block explorer to allow for community and security review.


### `QA-LIQUIDITY` — Liquidity withdrawable by the owner/deployer  *(Severity: High · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by the token's owner/deployer (0x0fa6…4eae) — they can pull that liquidity at any moment. This is the rug-pull path. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 44.8% of supply. What remains: 28.1% in wallets, 16.7% in other contracts. 503 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

503 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $93K (DexScreener, all pools). 24h trading volume $912K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mint capability could not be read. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $93K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x3545...63c2`](https://basescan.org/address/0x35453ab2b050b5f5ef586131c3ccd94ef89563c2) |
| **Network** | Base |
| **Price** | $0.00000253 |
| **24h Volume** | $912.4K |
| **Liquidity** | $93.1K |
| **Volume / Liquidity** | 9.8× |
| **Token Age** | 2h |
| **Top-10 Holders** | 44.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1332 buys / 1042 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0xc5c7baa9e8c1135274d5b014db0589ec76fe91a72e26b62b40a860a4ea306383)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/pangea-base-2a83)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-25*
