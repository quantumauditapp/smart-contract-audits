---
token: The Stonks Exchange
ticker: STONKEX
network: base
risk_score: 54
status: medium
date: 2026-11-06
---

# The Stonks Exchange (STONKEX) — Smart Contract Security Analysis | Base

> **Risk Score: 54/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/the-stonks-exchange-base-3069)

---

## Audit Summary

The contract at the provided address is not verified on the Base block explorer. Consequently, the source code is unavailable for security analysis. Investors should exercise extreme caution as the lack of transparency prevents verification of ownership, tax mechanisms, or potential backdoors.

> **Final Recommendation:** Do not interact with or provide liquidity to this contract. The lack of verified source code is a significant red flag that prevents any meaningful security assessment and exposes users to potential rug-pulls or malicious logic execution.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | 7.1 Architecture: Unknown. 7.2 Code Security: Unverifiable. 7.3 Access Control: Unverifiable. The absence of source code makes it impossible to assess the technical integrity or security posture of… |
| **Governance / Economics** | 4/10 | Medium | 7.4 Economic: Unverifiable. 7.5 Governance: Unverifiable. 7.6 External: Unverifiable. Without access to the contract logic, economic parameters such as minting capabilities or transfer taxes cannot… |
| **Upgrades** | 6/10 | Medium | 7.7 Upgrades: Unverifiable. 7.8 Operations: Unverifiable. It is impossible to determine if the contract is immutable or if it utilizes a proxy pattern that allows for logic changes post-deployment. |

## Security Findings

_🔴 1 Critical · ⚪ 5 Informational_

### `C-01` — Unverified Source Code  *(Severity: Critical · Status: Unresolved)*

The contract source code is not published on the block explorer, preventing any security audit or verification of contract behavior.

**Recommendation:** Verify the contract source code on the block explorer to allow for community and security review.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 18.7% of supply. What remains: 18.7% in wallets, 0.0% in other contracts. The deployer/owner wallet itself holds 15.3%. 720 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

720 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $135K (DexScreener, all pools). 24h trading volume $1.0M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mint capability could not be read. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $135K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x4faf...8111`](https://basescan.org/address/0x4faf2981ae2ef59295f14998108820e5ecc68111) |
| **Network** | Base |
| **Price** | $0.0004802 |
| **24h Volume** | $1.02M |
| **Liquidity** | $135.2K |
| **Volume / Liquidity** | 7.5× |
| **Token Age** | 10h |
| **Top-10 Holders** | 18.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1291 buys / 957 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0xf3b14b2c1ae230ffb3fdac99f74c44e95e8fa0c559691b09fc2b428c12953683)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/the-stonks-exchange-base-3069)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-06*
