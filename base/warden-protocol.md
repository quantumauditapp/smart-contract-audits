---
token: Warden Protocol
ticker: WRDN
network: base
risk_score: 78
status: high
date: 2026-10-27
---

# Warden Protocol (WRDN) — Smart Contract Security Analysis | Base

> **Risk Score: 78/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/warden-protocol-base)

---

## Audit Summary

The contract at the provided address is not verified on the Base block explorer. Consequently, the source code is unavailable for review, preventing any assessment of logic, security vulnerabilities, or backdoors. Investors should exercise extreme caution as unverified contracts carry the highest risk of rug pulls or malicious functionality.

> **Final Recommendation:** Do not interact with or provide liquidity to this contract. The lack of source code verification is a primary indicator of high-risk projects that lack transparency and accountability. 

If you are a token holder, consider the high probability of malicious intent, such as hidden minting functions, transfer blacklists, or liquidity withdrawal mechanisms. Prioritize assets with verified, audited, and open-source codebases.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | 7.1 Architecture: Unknown. 7.2 Code Security: Cannot be verified due to lack of source code. 7.3 Access Control: Cannot be audited. 7.6 External: Unknown dependencies. |
| **Governance / Economics** | 1/10 | High | 7.4 Economic: Tokenomics and tax mechanisms are opaque. 7.5 Governance: No insight into ownership or administrative privileges. 7.8 Operations: High risk of centralized control. |
| **Upgrades** | 5/10 | Medium | 7.7 Upgrades: Cannot determine if the contract is immutable or utilizes a proxy pattern. Without source verification, any upgradeability mechanism remains a hidden risk. |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🔴 1 Critical · 🟡 1 Medium · ⚪ 5 Informational_

### `C-01` — Contract Not Verified  *(Severity: Critical · Status: Unresolved)*

The contract source code is not published on the block explorer. It is impossible to verify the contract's logic, security, or adherence to standard token interfaces.

**Recommendation:** Publish and verify the source code on the block explorer to allow for community and security review.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a contract, 0x369d…2734 — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 90.5% of supply. Of that, 1.1% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 68.4% in wallets, 21.0% in other contracts. 1,744 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

1,744 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $68K (DexScreener, all pools). 24h trading volume $128K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mint capability could not be read. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $68K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x9779...45b7`](https://basescan.org/address/0x977963ea03f78cd203242983cd3878989b6a45b7) |
| **Network** | Base |
| **Price** | $0.01595 |
| **24h Volume** | $127.7K |
| **Liquidity** | $68.0K |
| **Volume / Liquidity** | 1.9× |
| **Token Age** | 17h |
| **Top-10 Holders** | 90.5% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1484 buys / 338 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0x2ca71d04cf467e11ea6870c6c63d395effac17f3)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/warden-protocol-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-27*
