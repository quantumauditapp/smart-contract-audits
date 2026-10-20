---
token: MERL
ticker: MERL
network: bsc
risk_score: 29
status: low
date: 2026-10-10
---

# MERL (MERL) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 29/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/merl-bsc)

---

## Audit Summary

This audit covers a `DelayedERC1967Proxy` contract on the BSC network. The contract is a UUPS proxy, meaning its logic can be upgraded. Ownership and control over upgrades are managed by a 2-of-3 multisig wallet. No critical or high-severity vulnerabilities were identified in the proxy's code itself.

> **Final Recommendation:** For a proxy contract, the primary security focus shifts to the implementation contract it points to and the upgrade process. It is crucial to ensure that any future implementation contracts undergo thorough security audits before deployment. Maintain strict operational security for the controlling multisig wallet, and consider implementing a time-lock for upgrade operations if not already present, to provide a window for community review and emergency intervention.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 9/10 | Low | 7.1 Architecture, 7.2 Code Security: The contract functions as a `DelayedERC1967Proxy`, a standard UUPS proxy pattern, delegating calls to an implementation contract. It explicitly lacks direct… |
| **Governance / Economics** | 5/10 | Medium | 7.3 Access Control, 7.4 Economic, 7.5 Governance: Access control for the proxy's administrative functions, such as upgrades, is managed by a multisig wallet (2 out of 3 owners), significantly… |
| **Upgrades** | 2/10 | High | 7.7 Upgrades: The contract utilizes the UUPS proxy pattern, enabling future upgrades of its logic implementation. The upgrade mechanism is controlled by the designated multisig owner. While the… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Uups |
| **Implementation** | ✅ Verified source |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 89.2% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 1 Medium · ⚪ 5 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 2 address(es) other than the owner/deployer. One of them — a wallet, 0x02c7…d10b — holds 89.2% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint/owner authority, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 66.4% of supply. Of that, 23.6% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 20.4% in wallets, 22.5% in other contracts. 17,920 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Merlin Chain (MERL), market cap $65M, rank #403. 17,920 holders. Verified by: CoinGecko.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $2.0M (DexScreener, all pools). 24h trading volume $6.4M (CoinGecko, all markets, daily snapshot). 24h trading volume $2.9M (DexScreener, all pools). CoinGecko's record for this coin: all-time high $1.45 on 2024-04-19; the price is now 97.8596% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mint capability could not be read. Control: a 2-of-3 multisig. Code: upgradeable proxy. Fees: no buy or sell tax. Market: $2.0M of DEX liquidity across 2 pools. Launch: 509 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xa0c5...07f9`](https://bscscan.com/address/0xa0c56a8c0692bd10b3fa8f8ba79cf5332b7107f9) |
| **Network** | BNB Chain |
| **Price** | $0.03115 |
| **24h Volume** | $2.92M |
| **Liquidity** | $2.02M |
| **Volume / Liquidity** | 1.4× |
| **Token Age** | 1y |
| **Top-10 Holders** | 66.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2834 buys / 3687 sells |

## Security Flags (1/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ⚠️ Unknown |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0xbdccafb234be6dc2545b0c25b0a5f5d9d1124228)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/merl-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-10*
