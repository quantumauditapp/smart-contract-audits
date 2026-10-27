---
token: A Gangstar Inu
ticker: AGI
network: bsc
risk_score: 64
status: medium
date: 2026-10-27
---

# A Gangstar Inu (AGI) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 64/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/a-gangstar-inu-bsc)

---

## Audit Summary

The contract at the provided address is not verified on the BSC block explorer. Consequently, the source code is unavailable for review, making it impossible to assess the logic, security, or safety of the contract. Investors should exercise extreme caution as unverified contracts often lack transparency and may contain malicious functions such as honeypot mechanisms or unauthorized minting capabilities.

> **Final Recommendation:** Do not interact with this contract. The inability to verify the source code prevents any meaningful security assurance and poses a critical risk of total loss of funds. If you are a token holder, consider the high probability of malicious intent associated with unverified smart contracts.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The technical architecture cannot be evaluated due to the lack of source code. 7.1 Architecture, 7.2 Code Security, 7.3 Access Control, 7.6 External, and 7.8 Operations are all considered high-risk.… |
| **Governance / Economics** | 1/10 | High | Economic parameters and governance structures are opaque. 7.4 Economic and 7.5 Governance items remain unverified. Users have no visibility into tax mechanisms, supply controls, or ownership… |
| **Upgrades** | 6/10 | Medium | The upgradeability status (7.7 Upgrades) is unknown. Without source code, it is impossible to determine if the contract is immutable or if it utilizes a proxy pattern that allows for arbitrary logic… |

## Security Findings

_🔴 1 Critical · ⚪ 5 Informational_

### `C-01` — Contract Not Verified  *(Severity: Critical · Status: Unresolved)*

The contract source code is not published on the block explorer. This prevents any security analysis, logic verification, or assessment of owner privileges.

**Recommendation:** Verify the contract source code on the block explorer to allow for public audit and transparency. If verification is not possible, the contract should be treated as untrusted.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 43.2% of supply. What remains: 7.8% in wallets, 35.3% in other contracts. 487 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

487 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $21K (DexScreener, all pools). 24h trading volume $473K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: meme vocabulary in name/ticker (inu). Tokenomics — Supply: mint capability could not be read. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $21K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x4000...177a`](https://bscscan.com/address/0x400067859346b77ee6a838e8ce6b8e712f96177a) |
| **Network** | BNB Chain |
| **Price** | $0.00004466 |
| **24h Volume** | $473.1K |
| **Liquidity** | $21.3K |
| **Volume / Liquidity** | 22.2× |
| **Token Age** | 9h |
| **Top-10 Holders** | 43.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 3765 buys / 2533 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x43ab18b3bef4e3e5b24fec5ea382bb7a7aa170cc)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/a-gangstar-inu-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-27*
