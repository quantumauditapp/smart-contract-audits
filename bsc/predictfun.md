---
token: Predict.fun
ticker: PREDICT
network: bsc
risk_score: 77
status: high
date: 2026-10-28
---

# Predict.fun (PREDICT) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 77/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/predictfun-bsc)

---

## Audit Summary

The contract at the provided address is not verified on the block explorer. Consequently, the source code is unavailable for security analysis. Investors should exercise extreme caution as the lack of transparency prevents verification of ownership, tax mechanisms, or liquidity lock status.

> **Final Recommendation:** Do not interact with this contract. Without verified source code, it is impossible to determine if the contract contains malicious functions such as honeypot mechanisms, unauthorized minting, or restricted selling. 

Prioritize assets that provide transparent, verified source code and audited documentation. If you are a holder, consider exiting positions immediately as the lack of transparency is a primary indicator of high-risk or fraudulent projects.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | 7.1 Architecture and 7.2 Code Security cannot be assessed due to the lack of verified source code. 7.3 Access Control is opaque, though the contract is controlled by an EOA. 7.6 External dependencies… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic and 7.5 Governance parameters are hidden from public view. The contract owner is an EOA, which poses a high centralization risk. There is no evidence of liquidity locks or renounced… |
| **Upgrades** | 6/10 | Medium | 7.7 Upgrades are not applicable as the contract is not a proxy. However, the inability to verify the code means hidden upgrade-like backdoors cannot be ruled out. |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Locked** | 100.0% — Null Address, PinkLock02 |

## Security Findings

_🔴 1 Critical · 🟠 1 High · ⚪ 6 Informational_

### `C-01` — Unverified Source Code  *(Severity: Critical · Status: Unresolved)*

The contract source code is not published on the block explorer. This prevents any security assessment of the contract logic.

**Recommendation:** Verify the contract source code on the block explorer to allow for community and security review.


### `H-02` — Centralized Ownership Risk  *(Severity: High · Status: Unresolved)*

The contract is owned by an EOA (0x34f0...), which has full control over administrative functions. Ownership has not been renounced.

**Recommendation:** Renounce ownership or transfer control to a multi-signature wallet or a time-locked governance contract.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 80.4% of supply. Of that, 1.1% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 79.3% in wallets, 0.0% in other contracts. 1,383 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

1,383 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity time-locked  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% is locked in PinkLock02 until 31 Oct 2027 (367 days). Until then nobody — the project included — can withdraw it unless the locker contract itself is flawed; after that date the lock's owner can.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $1.6M (DexScreener, all pools). 24h trading volume $247.3M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mint capability could not be read. Control: a single wallet (EOA). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $1.6M of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x79ad...7777`](https://bscscan.com/address/0x79ad05d307b465da8d0b4f1f1f6674dc7c097777) |
| **Network** | BNB Chain |
| **Price** | $0.0751 |
| **24h Volume** | $247.32M |
| **Liquidity** | $1.59M |
| **Volume / Liquidity** | 155.8× |
| **Token Age** | 6h |
| **Top-10 Holders** | 80.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2586 buys / 2449 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ❌ Fail |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ⚠️ Unknown |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ❌ | Source code is **not verified** — contract logic is opaque. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x05cd1b1ef2ee66a744699e78179bdccf2639fcd3)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/predictfun-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-28*
