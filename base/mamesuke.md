---
token: MAMESUKE
ticker: MAMESUKE
network: base
risk_score: 54
status: medium
date: 2026-11-04
---

# MAMESUKE (MAMESUKE) — Smart Contract Security Analysis | Base

> **Risk Score: 54/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/mamesuke-base)

---

## Audit Summary

The contract at the provided address is not verified on the Base block explorer. Consequently, the source code is unavailable for security review. Investors should exercise extreme caution as the lack of transparency prevents verification of ownership, tax mechanisms, or liquidity lock status.

> **Final Recommendation:** Do not interact with this contract until the source code is verified on the block explorer and audited by a reputable third party. Verify the contract's behavior through independent analysis of the deployed bytecode if you possess the necessary technical expertise.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The technical architecture cannot be assessed due to the lack of verified source code. 7.1 Architecture, 7.2 Code Security, 7.3 Access Control, and 7.6 External dependencies remain entirely opaque.… |
| **Governance / Economics** | 4/10 | Medium | Economic parameters such as 7.4 Economic sustainability and 7.5 Governance mechanisms are hidden from public view. There is no way to verify if the token has minting capabilities, transfer taxes, or… |
| **Upgrades** | 6/10 | Medium | 7.7 Upgrades and 7.8 Operations are unverifiable. It is unknown if the contract is immutable or if an owner can modify logic post-deployment. Users should assume the highest level of risk regarding… |

## Security Findings

_🔴 1 Critical · ⚪ 5 Informational_

### `C-01` — Unverified Contract Source  *(Severity: Critical · Status: Unresolved)*

The contract source code is not verified on the Base block explorer, preventing any security assessment of the logic, ownership, or tokenomics.

**Recommendation:** Verify the contract source code on the block explorer and provide a public audit report before soliciting user funds.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 16.7% of supply. What remains: 16.7% in wallets, 0.0% in other contracts. The deployer/owner wallet itself holds 12.0%. 672 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

672 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $178K (DexScreener, all pools). 24h trading volume $841K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mint capability could not be read. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $178K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x5409...e27c`](https://basescan.org/address/0x5409f59afeaecf5029fd4d5df9f4f8982d9fe27c) |
| **Network** | Base |
| **Price** | $0.0007903 |
| **24h Volume** | $840.9K |
| **Liquidity** | $178.0K |
| **Volume / Liquidity** | 4.7× |
| **Token Age** | 11h |
| **Top-10 Holders** | 16.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1161 buys / 829 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0x75298b7ce3deb3d49a8a4b3b19f2e8aec86bedc35f120adbad911ca03ecd45a9)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/mamesuke-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-04*
