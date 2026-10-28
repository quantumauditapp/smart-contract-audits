---
token: Agora
ticker: AGORA
network: bsc
risk_score: 59
status: medium
date: 2026-10-28
---

# Agora (AGORA) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 59/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/agora-bsc)

---

## Audit Summary

The contract at the provided address is not verified on the BSC block explorer. Consequently, the source code is inaccessible for security analysis. Investors should exercise extreme caution as the lack of transparency prevents verification of ownership, tax mechanisms, or potential backdoors.

> **Final Recommendation:** Do not interact with or invest in this contract until the source code is verified on the block explorer and audited by a reputable third party. The inability to inspect the contract logic poses a critical risk of total loss of funds.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The technical architecture cannot be evaluated due to the absence of verified source code. 7.1 Architecture, 7.2 Code Security, and 7.3 Access Control are entirely opaque. Without bytecode analysis… |
| **Governance / Economics** | 5/10 | Medium | Economic parameters such as 7.4 Economic and 7.5 Governance are unverifiable. There is no visibility into potential minting capabilities, transfer taxes, or liquidity lock mechanisms. Investors are… |
| **Upgrades** | 7/10 | Low | 7.7 Upgrades and 7.8 Operations cannot be assessed. It is unknown if the contract utilizes proxy patterns or immutable logic. The lack of verification suggests a high risk of hidden administrative… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Null Address |

## Security Findings

_🔴 1 Critical · 🟠 1 High · ⚪ 5 Informational_

### `C-01` — Unverified Source Code  *(Severity: Critical · Status: Unresolved)*

The contract source code is not published on the block explorer, preventing any security assessment of the logic.

**Recommendation:** Verify the contract source code on the block explorer to allow for community and security review.


### `H-02` — Lack of Transparency  *(Severity: High · Status: Unresolved)*

The absence of verified code makes it impossible to identify potential malicious functions such as honeypots, blacklists, or unauthorized minting.

**Recommendation:** Provide a link to the verified source code or documentation explaining the contract's functionality.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $25K (DexScreener, all pools). 24h trading volume $333K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mint capability could not be read. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: 2% on buy, 2.01% on sell. Market: $25K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x1170...825e`](https://bscscan.com/address/0x11705486b79c4e3ed6dda92967d898f69260825e) |
| **Network** | BNB Chain |
| **Price** | $0.0000649 |
| **24h Volume** | $333.3K |
| **Liquidity** | $24.9K |
| **Volume / Liquidity** | 13.4× |
| **Token Age** | 0h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 2.0% / 2.0% |
| **24h Transactions** | 2475 buys / 3913 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ❌ Fail |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ⚠️ Unknown |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ❌ | Source code is **not verified** — contract logic is opaque. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x31248470e019acf42c7b74c7ac98f00a107fcb59)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/agora-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-28*
