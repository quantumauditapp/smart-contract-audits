---
token: Luxor
ticker: LUX
network: arbitrum
risk_score: 74
status: high
date: 2026-11-04
---

# Luxor (LUX) — Smart Contract Security Analysis | Arbitrum

> **Risk Score: 74/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/luxor-arb)

---

## Audit Summary

The contract at the provided address is not verified on the Arbitrum block explorer. Consequently, the source code is inaccessible, preventing any technical security analysis. Investors should exercise extreme caution as the lack of transparency precludes verification of ownership, minting capabilities, or tax mechanisms.

> **Final Recommendation:** Do not interact with this contract. The lack of source code verification is a major red flag that prevents any form of security due diligence. Without transparency, there is no assurance regarding the safety of funds or the integrity of the contract logic.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The technical architecture cannot be evaluated due to the absence of verified source code. 7.1 Architecture, 7.2 Code Security, and 7.3 Access Control items remain entirely opaque. Without bytecode… |
| **Governance / Economics** | 1/10 | High | Economic parameters such as supply caps and tax logic are hidden from the user. 7.4 Economic and 7.5 Governance items cannot be assessed. Users are exposed to potential rug-pull risks, including… |
| **Upgrades** | 6/10 | Medium | The upgradeability status is unknown as the contract is not verified. 7.7 Upgrades items cannot be confirmed. There is no way to verify if the contract logic can be altered post-deployment. |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🔴 1 Critical · 🟡 1 Medium · ⚪ 5 Informational_

### `C-01` — Unverified Source Code  *(Severity: Critical · Status: Unresolved)*

The contract source code is not published on the block explorer, making it impossible to audit for vulnerabilities, backdoors, or malicious logic.

**Recommendation:** Publish and verify the source code on the block explorer to allow for community and security review.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a wallet, 0xbfc4…1bca — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 93.2% of supply. Of that, 2.4% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 90.8% in wallets, 0.0% in other contracts. The deployer/owner wallet itself holds 2.2%. 418 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

418 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $281K (DexScreener, all pools). 24h trading volume $136K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mint capability could not be read. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $281K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x56d9...d55f`](https://arbiscan.io/address/0x56d92aadd45791a8c9f5010f15f070f88453d55f) |
| **Network** | Arbitrum |
| **Price** | $0.06531 |
| **24h Volume** | $136.4K |
| **Liquidity** | $280.7K |
| **Volume / Liquidity** | 0.5× |
| **Token Age** | 5h |
| **Top-10 Holders** | 93.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 636 buys / 245 sells |

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

- [View on DexScreener](https://dexscreener.com/arbitrum/0x8fe37ae0703b23261fcdb6c8f2f1fb9cffd754e5)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/luxor-arb)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-04*
