---
token: Forta
ticker: FORT
network: polygon
risk_score: 68
status: high
date: 2026-10-20
---

# Forta (FORT) — Smart Contract Security Analysis | Polygon

> **Risk Score: 68/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/forta-poly)

---

## Audit Summary

The contract is a standard EIP-1967 proxy implementation used to delegate calls to an underlying logic contract. The proxy itself contains no business logic, state variables, or privileged functions, serving purely as a transparent forwarding layer. No vulnerabilities were identified in the proxy structure itself.

> **Final Recommendation:** As this is a standard proxy contract, ensure that the implementation contract (0xd6b3139108e271c812acc6ffebad28e935d61e24) is audited for business logic and access control vulnerabilities. Future upgrades should be performed through a multi-signature wallet or a decentralized governance contract to mitigate centralization risks.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The architecture follows the standard EIP-1967 proxy pattern, ensuring clean separation between the proxy and implementation. 7.1 Architecture is robust, utilizing standard storage slots to prevent… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic and 7.5 Governance items are not applicable as the proxy contract holds no assets and contains no governance logic. The contract acts strictly as a forwarding mechanism. All economic… |
| **Upgrades** | 3/10 | High | 7.7 Upgrades are managed via the standard EIP-1967 storage slot mechanism. The proxy supports secure implementation updates if the underlying logic contract includes appropriate access control. No… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Uups |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 58.6% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 1 Medium · ⚪ 5 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 3 address(es) other than the owner/deployer. One of them — a contract, 0xa570…8698 — holds 58.6% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 82.0% of supply. Of that, 2.5% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 36.2% in wallets, 43.2% in other contracts. 3,188 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Forta (FORT), market cap $14M, rank #995. 3,188 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $24K (DexScreener, all pools). 24h trading volume $1.6M (CoinGecko, all markets, daily snapshot). 24h trading volume $46K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $0.965 on 2022-06-15; the price is now 97.6996% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mint capability could not be read. Control: an owner that could not be resolved. Code: upgradeable proxy. Fees: no buy or sell tax. Market: $24K of DEX liquidity across 2 pools. Launch: 1550 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x9ff6...d3e1`](https://polygonscan.com/address/0x9ff62d1fc52a907b6dcba8077c2ddca6e6a9d3e1) |
| **Network** | Polygon |
| **Price** | $0.02169 |
| **24h Volume** | $46.1K |
| **Liquidity** | $24.2K |
| **Volume / Liquidity** | 1.9× |
| **Token Age** | 4y |
| **Top-10 Holders** | 82.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 475 buys / 650 sells |

## Security Flags (1/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ⚠️ Unknown |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Sources

- [View on DexScreener](https://dexscreener.com/polygon/0xc014e3c42bd6896b8533d457af7263648a3f5239)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/forta-poly)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-20*
