---
token: Surplus Intelligence
ticker: SURPLUS
network: base
risk_score: 78
status: high
date: 2026-10-27
---

# Surplus Intelligence (SURPLUS) — Smart Contract Security Analysis | Base

> **Risk Score: 78/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/surplus-intelligence-base-ecca)

---

## Audit Summary

The contract at the provided address is not verified on the Base block explorer. Consequently, the source code is unavailable for inspection, preventing any analysis of logic, security vulnerabilities, or backdoors. Users should exercise extreme caution as the lack of transparency is a significant indicator of potential malicious intent or negligence.

> **Final Recommendation:** Do not interact with this contract. The lack of source code verification is a major red flag that prevents any form of security due diligence. Without verified code, there is no way to ensure the safety of your funds or the legitimacy of the token's economic model.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | 7.1 Architecture: Unknown. 7.2 Code Security: Unverifiable. 7.3 Access Control: Unverifiable. The absence of source code makes it impossible to assess the technical integrity of the contract. No… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic: Unverifiable. 7.5 Governance: Unverifiable. 7.6 External: Unverifiable. Without access to the contract logic, it is impossible to determine if there are hidden minting functions, tax… |
| **Upgrades** | 6/10 | Medium | 7.7 Upgrades: Unverifiable. 7.8 Operations: Unverifiable. It is unknown if the contract utilizes a proxy pattern or if the owner has the ability to modify contract logic post-deployment. |

## Security Findings

_🔴 1 Critical · 🟠 1 High · ⚪ 4 Informational_

### `C-01` — Unverified Contract Source Code  *(Severity: Critical · Status: Unresolved)*

The contract source code is not published on the block explorer, making it impossible to audit for vulnerabilities, backdoors, or malicious logic.

**Recommendation:** Verify the contract source code on the block explorer to allow for public transparency and security assessment.


### `QA-HOLDERS` — Who holds the supply  *(Severity: High · Status: Acknowledged)*

The ten largest holders own 70.3% of supply. What remains: 70.3% in wallets, 0.0% in other contracts. The deployer/owner wallet itself holds 42.5%. A holder that also controls the contract can sell into its own liquidity. 360 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

360 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $43K (DexScreener, all pools). 24h trading volume $149K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mint capability could not be read. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $43K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x60de...45e1`](https://basescan.org/address/0x60de0fb4d6dccbb9fbbba95f89e82626facd45e1) |
| **Network** | Base |
| **Price** | $0.00006414 |
| **24h Volume** | $148.7K |
| **Liquidity** | $42.9K |
| **Volume / Liquidity** | 3.5× |
| **Token Age** | 15h |
| **Top-10 Holders** | 70.3% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 996 buys / 705 sells |

## Security Flags (1/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ❌ Fail |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ⚠️ Unknown |
| Liquidity Locked | ⚠️ Unknown |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ❌ | Source code is **not verified** — contract logic is opaque. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| Liquidity Locked | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/base/0xed8b1495358b316aeb3ff90cab5d934a8449977b5e41b9b784c42c9c00f78a93)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/surplus-intelligence-base-ecca)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-27*
