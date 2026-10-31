---
token: Mural
ticker: MUR
network: arbitrum
risk_score: 75
status: high
date: 2026-10-31
---

# Mural (MUR) — Smart Contract Security Analysis | Arbitrum

> **Risk Score: 75/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/mural-arb)

---

## Audit Summary

The contract at the provided address is not verified on the Arbitrum block explorer. Consequently, the source code is inaccessible, and no technical audit of the logic, security, or tokenomics can be performed. Investors should exercise extreme caution as unverified contracts often lack transparency and may contain malicious functions such as honeypots or unauthorized minting capabilities.

> **Final Recommendation:** Do not interact with or provide liquidity to this contract. Without verified source code, there is no assurance that the contract functions as intended or that funds are secure from malicious actors.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | 7.1 Architecture: Unknown. 7.2 Code Security: Cannot be verified due to lack of source code. 7.3 Access Control: Cannot be verified. 7.6 External: Unknown integration risks. |
| **Governance / Economics** | 1/10 | High | 7.4 Economic: Tokenomics and supply mechanics are opaque. 7.5 Governance: No information on ownership or administrative controls. 7.8 Operations: High risk of rug-pull or liquidity withdrawal. |
| **Upgrades** | 6/10 | Medium | 7.7 Upgrades: Cannot determine if the contract is immutable or utilizes a proxy pattern. Without source code, any potential upgradeability remains a hidden risk. |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 99.8% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🔴 1 Critical · 🟡 1 Medium · ⚪ 5 Informational_

### `C-01` — Unverified Contract Source Code  *(Severity: Critical · Status: Unresolved)*

The contract source code is not published on the block explorer, preventing any security analysis or verification of token mechanics.

**Recommendation:** Publish the source code on the block explorer and undergo a professional security audit before soliciting user interaction.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 2 address(es) other than the owner/deployer. One of them — a wallet, 0x59c8…424b — holds 99.8% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 93.8% of supply. What remains: 93.8% in wallets, 0.0% in other contracts. The deployer/owner wallet itself holds 2.0%. 410 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

410 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $67K (DexScreener, all pools). 24h trading volume $121K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mint capability could not be read. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $67K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x086d...62c7`](https://arbiscan.io/address/0x086d1345b5cc7f7e147acb7dbed19bc38a7d62c7) |
| **Network** | Arbitrum |
| **Price** | $0.06394 |
| **24h Volume** | $121.4K |
| **Liquidity** | $66.7K |
| **Volume / Liquidity** | 1.8× |
| **Token Age** | 11h |
| **Top-10 Holders** | 93.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 744 buys / 248 sells |

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

- [View on DexScreener](https://dexscreener.com/arbitrum/0x769d0df063355d0d2c26d6a606ace3b352e4750f)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/mural-arb)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-31*
