---
token: STONKCAT
ticker: STONKCAT
network: base
risk_score: 56
status: medium
date: 2026-10-03
---

# STONKCAT (STONKCAT) — Smart Contract Security Analysis | Base

> **Risk Score: 56/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/stonkcat-base)

---

## Audit Summary

The StonkToken contract is a standard ERC-20 token implementation with no custom logic or privileged functions. The audit found no critical, high, medium, or low-severity vulnerabilities, indicating a robust and secure design for its intended purpose.

> **Final Recommendation:** Given the contract's simplicity as a standard ERC-20 token with no custom logic or privileged functions, the primary recommendation is to ensure the token's integration with any external systems or dApps is handled securely. Developers should verify that all interactions with the StonkToken contract adhere to the ERC-20 standard and account for potential reentrancy or approval-related issues in their own calling contracts. No specific security enhancements are required for the StonkToken contract itself.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The StonkToken contract implements the ERC-20 standard without any additional custom logic or privileged functions (7.1 Architecture). All standard ERC-20 functions like `transfer` and `approve` are… |
| **Governance / Economics** | 6/10 | Medium | The StonkToken contract exhibits minimal governance and economic risk due to its design as a pure ERC-20 token without any administrative privileges or special economic mechanisms (7.4 Economic).… |
| **Upgrades** | 8/10 | Low | The StonkToken contract is not designed as an upgradeable proxy (7.7 Upgrades). It is a standard, immutable contract deployed directly to the blockchain. This design choice eliminates all risks… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 88.3% |
| **Top-3 Unlocked** | ⚠️ 99.9% |

## Security Findings

_🟡 1 Medium · ⚪ 6 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 3 address(es) other than the owner/deployer. One of them — a wallet, 0x49a5…349c — holds 88.4% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 57.2% of supply. What remains: 0.0% in wallets, 57.2% in other contracts. The deployer/owner wallet itself holds 1.6%. 193 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

193 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $19K (DexScreener, all pools). 24h trading volume $61K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: meme vocabulary in name/ticker (cat). Tokenomics — Supply: fixed — the contract has no mint function. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $19K of DEX liquidity across 13 pools. Launch: 1 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 1 day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 1 day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x982e...bd11`](https://basescan.org/address/0x982e673489b48c22488ec7fb21daf4967738bd11) |
| **Network** | Base |
| **Price** | $0.00003639 |
| **24h Volume** | $60.5K |
| **Liquidity** | $19.3K |
| **Volume / Liquidity** | 3.1× |
| **Token Age** | 1d |
| **Top-10 Holders** | 57.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 428 buys / 378 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/base/0xd92e348e2af0ee2a9e3750ff285150d6cb21a5eb)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/stonkcat-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-03*
