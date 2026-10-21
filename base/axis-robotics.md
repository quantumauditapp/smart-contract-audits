---
token: Axis Robotics
ticker: AXIS
network: base
risk_score: 36
status: medium
date: 2026-10-21
---

# Axis Robotics (AXIS) — Smart Contract Security Analysis | Base

> **Risk Score: 36/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/axis-robotics-base)

---

## Audit Summary

The AxisToken implementation contract deployed behind a UUPS ERC1967 proxy on Base was evaluated. The codebase adheres closely to standard OpenZeppelin upgradeable contracts, implementing ERC-20, ERC-20 Permit, and UUPS interfaces. Ownership of the privileged functions is held by a timelock contract with a 48-hour delay, significantly mitigating operational and administrative abuse risks.

> **Final Recommendation:** Maintain the current timelock configuration of 48 hours for any administration and upgrade execution to preserve user trust and verification windows. Consider establishing an absolute programmatic cap on total supply within the implementation contract or enforcing event notifications on pending minting proposals to ensure complete economic predictability.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 7/10 | Low | Regarding 7.1 Architecture and 7.2 Code Security, the contract relies on standard OpenZeppelin library patterns for ERC-20 and ERC-20 Permit logic with clean modularity. Standard transfers and… |
| **Governance / Economics** | 6/10 | Medium | Under 7.3 Access Control and 7.5 Governance, the contract assigns administrative powers to a Timelock controller with a 172,800-second (48-hour) minimum execution delay, preventing instantaneous rug… |
| **Upgrades** | 1/10 | High | For 7.7 Upgrades, the implementation utilizes the standard UUPS proxy pattern (IERC1822Proxiable/UUPSUpgradeable), ensuring upgrade logic is contained within the implementation and protected by… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Uups |
| **Implementation** | ✅ Verified source |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | 31.8% |
| **Top-3 Unlocked** | 58.6% |

## Security Findings

_🟡 2 Medium · ⚪ 6 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 94.7% is held, unlocked, by 10 address(es) other than the owner/deployer. No single one holds a majority: their exits thin the market rather than hand anyone the pool. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them. This assessment covers the main pool, which holds 72% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-POWERS` — What the token's controller can do  *(Severity: Medium · Status: Acknowledged)*

The contract lets its controller — a timelock with a 48h delay — mint new supply. Nothing independent vouches for whoever holds them, so each is a live risk to holders.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint/owner authority, mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 97.8% of supply. What remains: 5.4% in wallets, 92.4% in other contracts. 10,650 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Axis Robotics (AXIS). Traded on Coinbase. 10,650 holders. Verified by: exchange listings.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $3.4M (DexScreener, all pools). 24h trading volume $30.9M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: a timelock with a 48h delay. Code: upgradeable proxy. Fees: no buy or sell tax. Market: $3.4M of DEX liquidity across 30 pools. Launch: 2 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 2 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 2 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x5be7...55ea`](https://basescan.org/address/0x5be75e3b0aff5d1a042a5363ae36acb1d6d755ea) |
| **Network** | Base |
| **Price** | $0.2562 |
| **24h Volume** | $20.18M |
| **Liquidity** | $2.47M |
| **Volume / Liquidity** | 8.2× |
| **Token Age** | 2d |
| **Top-10 Holders** | 97.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 31474 buys / 38374 sells |

## Security Flags (1/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Sources

- [View on DexScreener](https://dexscreener.com/base/0xc19d91d99afc0332e5013a569c9721cd9ecb51a14c851f7a189a140950a627fa)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/axis-robotics-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-21*
