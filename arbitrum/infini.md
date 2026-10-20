---
token: Infini
ticker: IFN
network: arbitrum
risk_score: 74
status: high
date: 2026-10-04
---

# Infini (IFN) — Smart Contract Security Analysis | Arbitrum

> **Risk Score: 74/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/infini-arb)

---

## Audit Summary

No source code was provided for analysis. This report is based solely on the limited information available from the prefill data. A comprehensive security assessment requires access to the full contract source code to identify potential vulnerabilities and ensure adherence to security best practices.

> **Final Recommendation:** To ensure the security and integrity of the contract, it is strongly recommended to provide the full source code for a comprehensive audit. This would allow for a thorough examination of all potential vulnerabilities, adherence to best practices, and a complete assessment of the contract's design and implementation.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | Without access to the contract's source code, a detailed technical analysis of its architecture, code security, and access control mechanisms (7.1, 7.2, 7.3) cannot be performed. Therefore, no… |
| **Governance / Economics** | 1/10 | High | The economic model and governance structure (7.4, 7.5) of the contract cannot be assessed without the underlying source code. Potential risks related to tokenomics, flash loan vulnerabilities, or… |
| **Upgrades** | 6/10 | Medium | Without source code, it is impossible to determine if the contract employs an upgrade mechanism (7.7) or if it is immutable. Therefore, no assessment of upgrade safety, proxy patterns, or potential… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 99.7% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 1 Medium · ⚪ 6 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 2 address(es) other than the owner/deployer. One of them — a wallet, 0x0662…f13b — holds 99.7% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `I-01` — No code-level findings — contract source is not verified on the explorer  *(Severity: Informational · Status: Acknowledged)*

The contract's source code has not been published or verified on the block explorer, so only its deployed bytecode and on-chain behaviour were available. No source-level vulnerability could be confirmed or ruled out. The assessment on this page rests on holder concentration.

**Recommendation:** Treat an unverified contract as unaudited at the code level. Ask the team to verify the source on the explorer, which makes an independent review possible.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 93.5% of supply. What remains: 93.5% in wallets, 0.0% in other contracts. The deployer/owner wallet itself holds 2.4%. 409 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

409 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $87K (DexScreener, all pools). 24h trading volume $178K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mint capability could not be read. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $87K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xe877...bf7f`](https://arbiscan.io/address/0xe877ae9a2f792d5afa9359a79cdbb9506f05bf7f) |
| **Network** | Arbitrum |
| **Price** | $0.1913 |
| **24h Volume** | $178.3K |
| **Liquidity** | $86.7K |
| **Volume / Liquidity** | 2.1× |
| **Token Age** | 23h |
| **Top-10 Holders** | 93.5% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 823 buys / 296 sells |

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

- [View on DexScreener](https://dexscreener.com/arbitrum/0x94c5085f11160635c6551dfc1a3b68f5aa7f520e)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/infini-arb)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-04*
