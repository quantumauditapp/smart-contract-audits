---
token: DENIM
ticker: DENIM
network: base
risk_score: 27
status: low
date: 2026-11-05
---

# DENIM (DENIM) — Smart Contract Security Analysis | Base

> **Risk Score: 27/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/denim-base-9449)

---

## Audit Summary

The TaxLaunchToken is a standard ERC-20 implementation with additional metadata management and dividend initialization capabilities. The contract follows standard patterns for token transfers and utilizes restricted access control for administrative functions. No critical or high-severity vulnerabilities were identified during the static analysis of the provided source code.

> **Final Recommendation:** The contract is secure for deployment as it stands. Ensure that the addresses assigned to the 'factory' and 'metadataauthority' roles are secured with multi-signature wallets to prevent unauthorized changes to token metadata or dividend configurations.

Maintain strict operational security for the private keys associated with the administrative roles. Since the contract is immutable, any errors in the initial configuration of the dividend contract cannot be rectified post-deployment.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The architecture follows standard ERC-20 patterns with clean separation of concerns for metadata updates. 7.1 Architecture is robust, utilizing standard inheritance. 7.2 Code Security is high, with… |
| **Governance / Economics** | 2/10 | High | 7.4 Economic and 7.5 Governance aspects are centralized within the factory and metadata authority roles. The dividend initialization logic ensures the dividend contract is correctly configured before… |
| **Upgrades** | 6/10 | Medium | 7.7 Upgrades are not supported as the contract is not a proxy. 7.8 Operations are straightforward, with administrative functions limited to metadata updates and initial configuration. The lack of… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 59.6% |
| **Top-3 Unlocked** | ⚠️ 97.6% |

## Security Findings

_🟡 1 Medium · ⚪ 5 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 5 address(es) other than the owner/deployer. One of them — a wallet, 0xe397…2bee — holds 59.6% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint capability) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $35K (DexScreener, all pools). 24h trading volume $165K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $35K of DEX liquidity across 6 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xafda...cccc`](https://basescan.org/address/0xafda71a7060018bb052c73cac5881f059ffecccc) |
| **Network** | Base |
| **Price** | $0.00009937 |
| **24h Volume** | $164.0K |
| **Liquidity** | $34.7K |
| **Volume / Liquidity** | 4.7× |
| **Token Age** | 0h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1028 buys / 812 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0x120146a10fc69bb35006572c086e5618a42f8814a1aa62876c561e93d6fc951b)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/denim-base-9449)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-05*
