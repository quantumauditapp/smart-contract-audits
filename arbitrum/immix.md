---
token: Immix
ticker: IMMIX
network: arbitrum
risk_score: 76
status: high
date: 2026-10-20
---

# Immix (IMMIX) — Smart Contract Security Analysis | Arbitrum

> **Risk Score: 76/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/immix-arb)

---

## Audit Summary

The provided contract address is not verified on the Arbitrum block explorer. No source code was available for analysis, rendering the protocol's security posture impossible to verify. Immediate verification and a comprehensive audit are required before any capital deployment.

> **Final Recommendation:** Do not interact with this contract address. Verify the source code on the block explorer and perform a professional security audit before considering any integration or fund deposit.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | 7.1 Architecture and 7.2 Code Security cannot be assessed without source code. 7.3 Access Control and 7.6 External dependencies are currently opaque. The lack of transparency prevents any validation… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic and 7.5 Governance models are unknown. Without documentation or code, the risk of rug-pulls or malicious governance parameters remains at maximum. No economic safety guarantees exist. |
| **Upgrades** | 6/10 | Medium | 7.7 Upgrades and 7.8 Operations are unverified. It is unknown if the contract utilizes proxy patterns or immutable logic. The potential for hidden backdoors or unauthorized upgrades is high. |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 99.8% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🔴 1 Critical · 🟡 1 Medium · ⚪ 5 Informational_

### `C-01` — Unverified Contract Source  *(Severity: Critical · Status: Unresolved)*

The contract at the provided address is not verified on the blockchain explorer, preventing any security analysis or logic verification.

**Recommendation:** Verify the contract source code on the Arbitrum block explorer immediately.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 2 address(es) other than the owner/deployer. One of them — a wallet, 0xbde4…0c9d — holds 99.8% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 93.3% of supply. What remains: 90.9% in wallets, 2.4% in other contracts. The deployer/owner wallet itself holds 2.4%. 417 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

417 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $83K (DexScreener, all pools). 24h trading volume $129K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mint capability could not be read. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $83K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xb3a3...4f47`](https://arbiscan.io/address/0xb3a3d76393732210b67ce86b33f42a0856d84f47) |
| **Network** | Arbitrum |
| **Price** | $0.09923 |
| **24h Volume** | $129.3K |
| **Liquidity** | $83.2K |
| **Volume / Liquidity** | 1.6× |
| **Token Age** | 14h |
| **Top-10 Holders** | 93.3% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 811 buys / 283 sells |

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

- [View on DexScreener](https://dexscreener.com/arbitrum/0xf88c745b7e7c7a5f594d8b23639187484d345403)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/immix-arb)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-20*
