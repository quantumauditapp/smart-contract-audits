---
token: Dispatch
ticker: DSP
network: base
risk_score: 83
status: high
date: 2026-10-25
---

# Dispatch (DSP) — Smart Contract Security Analysis | Base

> **Risk Score: 83/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/dispatch-base-a794)

---

## Audit Summary

The contract at the provided address is not verified on the Base block explorer. Consequently, the source code is inaccessible, and no technical security assessment could be performed. Investors should exercise extreme caution as unverified contracts may contain malicious logic, including backdoors, honeypot mechanisms, or unrestricted minting capabilities.

> **Final Recommendation:** Do not interact with or provide liquidity to this contract until the source code is verified on the block explorer and audited by a reputable third party. Verify the contract's behavior through independent analysis of its bytecode if necessary, but prioritize transparency from the project team.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | 7.1 Architecture: Unknown. 7.2 Code Security: Inaccessible due to lack of verification. 7.3 Access Control: Cannot be verified, posing a high risk of unauthorized administrative actions. 7.6… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic: Tokenomics and supply mechanics are opaque. 7.5 Governance: No insight into ownership or upgradeability. 7.8 Operations: Lack of transparency prevents assessment of operational security. |
| **Upgrades** | 5/10 | Medium | 7.7 Upgrades: It is impossible to determine if the contract is a proxy or if it contains upgrade logic. Without verification, the contract could be swapped or modified if it utilizes a proxy pattern. |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🔴 1 Critical · 🟠 1 High · ⚪ 5 Informational_

### `C-01` — Unverified Source Code  *(Severity: Critical · Status: Unresolved)*

The contract source code is not published on the block explorer. This prevents any verification of the contract's logic, security posture, or intended functionality.

**Recommendation:** Publish the source code on the block explorer and ensure it matches the deployed bytecode to allow for community and security review.


### `QA-LIQUIDITY` — Liquidity withdrawable by the owner/deployer  *(Severity: High · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by the token's owner/deployer (0x6d79…9912) — they can pull that liquidity at any moment. This is the rug-pull path. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 29.6% of supply. What remains: 9.8% in wallets, 19.8% in other contracts. 762 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

762 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $95K (DexScreener, all pools). 24h trading volume $2.8M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mint capability could not be read. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $95K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xc9bc...0209`](https://basescan.org/address/0xc9bc896d9bc8bc7cc7917c147f115685dfb90209) |
| **Network** | Base |
| **Price** | $0.0003231 |
| **24h Volume** | $2.76M |
| **Liquidity** | $95.1K |
| **Volume / Liquidity** | 29.0× |
| **Token Age** | 19h |
| **Top-10 Holders** | 29.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2953 buys / 2178 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0x79bbba771657cda9254f5be366e177563ca188f2d73e7fdf16ca0a6cac31eb45)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/dispatch-base-a794)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-25*
