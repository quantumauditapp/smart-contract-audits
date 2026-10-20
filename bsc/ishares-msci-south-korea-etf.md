---
token: iShares MSCI South Korea ETF
ticker: EWYB
network: bsc
risk_score: 83
status: high
date: 2026-10-20
---

# iShares MSCI South Korea ETF (EWYB) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 83/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/ishares-msci-south-korea-etf-bsc)

---

## Audit Summary

The SecuritiesToken is an upgradeable ERC-20 implementation designed for regulated asset issuance. It utilizes a robust role-based access control system and modular compliance/pause logic. While the architecture is modular, the high degree of administrative control over core transfer logic and external dependencies introduces significant centralization risks.

> **Final Recommendation:** To mitigate centralization risks, it is recommended to transition administrative roles to a multi-signature wallet or a decentralized governance contract. This ensures that critical changes to compliance, pause managers, and economic multipliers require consensus rather than a single point of failure.

Additionally, implement a timelock mechanism for all sensitive administrative functions. This provides transparency and allows users to react to significant changes in token logic or economic parameters before they take effect.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract follows standard OpenZeppelin upgradeable patterns (7.1 Architecture) and implements secure ERC-20 logic (7.2 Code Security). Access control is strictly enforced via… |
| **Governance / Economics** | 1/10 | High | Governance is centralized under administrative roles (7.5 Governance). Economic parameters like transfer fees and UI multipliers are fully adjustable by privileged roles (7.4 Economic). This allows… |
| **Upgrades** | 1/10 | High | The contract utilizes a Beacon proxy pattern (7.7 Upgrades), allowing for standardized upgrades across multiple instances. Operations (7.8 Operations) are well-defined through explicit setter… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Beacon |
| **Implementation** | ✅ Verified source |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | 31.6% |
| **Top-3 Unlocked** | 67.2% |

## Security Findings

_🟠 1 High · 🟡 2 Medium · 🟢 1 Low · ⚪ 5 Informational_

### `CP-03` — Centralized Control Over Token Logic  *(Severity: High · Status: Unresolved)*

The contract allows a privileged role to change the addresses of the Compliance and PauseManager contracts. Because all token transfers depend on these external contracts, an administrator can effectively halt all transfers or bypass compliance checks at will.

**Recommendation:** Implement a multi-signature wallet for the administrative role and consider adding a timelock to any function that updates critical external contract dependencies.


### `CP-07` — Administrative Control Over Transfer Fees  *(Severity: Medium · Status: Unresolved)*

The setUIMultiplier function allows privileged roles to modify the transfer fee structure. This gives the administrator the ability to change the cost of moving tokens without prior notice to token holders.

**Recommendation:** Document the fee adjustment policy clearly and implement a notice period or a cap on how frequently or drastically fees can be adjusted.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 96.4% is held, unlocked, by 10 address(es) other than the owner/deployer. No single one holds a majority: their exits thin the market rather than hand anyone the pool. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `CP-08` — Administrative Control Over Transfer Limits  *(Severity: Low · Status: Unresolved)*

Privileged roles can modify numeric limits related to transaction sizes or wallet thresholds via the setUIMultiplier function. This allows the administrator to restrict or enable specific transfer behaviors arbitrarily.

**Recommendation:** Ensure that any changes to transfer limits are communicated to the community and governed by a transparent policy.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 99.4% of supply. Of that, 1.2% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 96.3% in wallets, 1.9% in other contracts. 3,658 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as iShares MSCI South Korea ETF (bStocks Tokenized Stock) (EWYB), market cap $10M, rank #1193. 3,658 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $222K (DexScreener, all pools). 24h trading volume $5.0M (CoinGecko, all markets, daily snapshot). 24h trading volume $1.2M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Tokenized real-world asset  *(Severity: Informational · Status: Acknowledged)*

A token backed by an off-chain asset (a stock, gold, treasury bills, a fund share) held by a named issuer or custodian. Issuance, redemption and transfer restrictions are the issuer's by design. The class itself adds no points; the contract and market facts decide the score. Basis: CoinGecko category: Tokenized Exchange-Traded Funds (ETFs). Tokenomics — Supply: mintable with no on-chain cap found. Control: an owner that could not be resolved. Code: upgradeable proxy. Fees: no buy or sell tax. Market: $222K of DEX liquidity across 30 pools. Launch: 5 days of market history.

**Recommendation:** Treat the issuer or custodian as the counterparty: check its custody reports and who may hold or redeem the token.


### `QA-RECENT` — Recently launched — 5 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 5 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xbe82...2cb8`](https://bscscan.com/address/0xbe82f76637dba2c114c41df856c2c51e522e2cb8) |
| **Network** | BNB Chain |
| **Price** | $157.0980 |
| **24h Volume** | $1.19M |
| **Liquidity** | $221.9K |
| **Volume / Liquidity** | 5.4× |
| **Token Age** | 5d |
| **Top-10 Holders** | 99.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 6069 buys / 6115 sells |

## Security Flags (1/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0xc60ed5b770e8a3abd60ee9ed10faa0aee577a66b)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/ishares-msci-south-korea-etf-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-20*
