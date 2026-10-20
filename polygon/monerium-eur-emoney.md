---
token: Monerium EUR emoney
ticker: EURE
network: polygon
risk_score: 21
status: low
date: 2026-10-20
---

# Monerium EUR emoney (EURE) — Smart Contract Security Analysis | Polygon

> **Risk Score: 21/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/monerium-eur-emoney-poly)

---

## Audit Summary

The PolygonPosEUR contract is a standard ERC-20 token implementation designed for the Polygon PoS bridge. It utilizes a controller-based architecture to manage transfer logic and role-based access control for minting and deposits. The contract is managed by a multisig wallet, providing a robust security baseline for administrative actions.

> **Final Recommendation:** The protocol demonstrates a high standard of security through its use of established bridge patterns and multisig governance. No vulnerabilities were identified in the current implementation.

Maintain the multisig threshold and ensure that any future controller contract updates undergo rigorous testing and independent security review before deployment, as the controller holds significant authority over token transfer logic.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The architecture follows standard bridge-compatible token patterns, separating core logic from a configurable controller. 7.1 Architecture and 7.2 Code Security are well-implemented, utilizing… |
| **Governance / Economics** | 4/10 | Medium | 7.4 Economic and 7.5 Governance aspects are centralized under a multisig controller. The owner can update the controller contract, which dictates transfer fees and logic, representing a significant… |
| **Upgrades** | 7/10 | Low | 7.7 Upgrades are handled via the controller pattern, allowing for logic updates without replacing the token contract itself. 7.8 Operations are supported by standard recovery functions for ether and… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | 39.9% |
| **Top-3 Unlocked** | ⚠️ 85.9% |

## Security Findings

_🟠 1 High · 🟡 1 Medium · ⚪ 5 Informational_

### `QA-POWERS` — What the token's controller can do  *(Severity: High · Status: Acknowledged)*

The contract lets its controller — a 3-of-6 multisig — pause all transfers. Nothing independent vouches for whoever holds them, so each is a live risk to holders.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 7 address(es) other than the owner/deployer. No single one holds a majority: their exits thin the market rather than hand anyone the pool. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them. This assessment covers the main pool, which holds 35% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint/owner authority, mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 15.2% of supply. Of that, 4.9% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 1.9% in wallets, 8.4% in other contracts. 3,598 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Monerium EUR emoney [OLD] (EURE), market cap $26M, rank #719. 3,598 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $180K (DexScreener, all pools). 24h trading volume $286K (CoinGecko, all markets, daily snapshot). 24h trading volume $50K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Stablecoin — issuer-backed (fiat reserves)  *(Severity: Informational · Status: Acknowledged)*

A token designed to hold a fixed value (usually $1). Its safety rests on what backs it and on who can mint, freeze or pause it. Its identity is not independently verified, so it gets none of the allowances an established stablecoin gets: every power its owner holds over supply and transfers is scored in full, because a peg is only as good as whoever can mint. Basis: CoinGecko category: EUR Stablecoin. Tokenomics — Supply: fixed — the contract has no mint function. Control: a 3-of-6 multisig. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $180K of DEX liquidity across 4 pools. Launch: 1374 days of market history.

**Recommendation:** Check what backs the peg and who controls supply: reserve attestations for an issuer-backed coin, collateral and governance for a protocol coin.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x18ec...04f6`](https://polygonscan.com/address/0x18ec0a6e18e5bc3784fdd3a3634b31245ab704f6) |
| **Network** | Polygon |
| **Price** | $1.1200 |
| **24h Volume** | $43.2K |
| **Liquidity** | $62.2K |
| **Volume / Liquidity** | 0.7× |
| **Token Age** | 3y |
| **Top-10 Holders** | 15.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 50 buys / 98 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/polygon/0x368a930b71326e3f640df36378d931dbe3d03746)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/monerium-eur-emoney-poly)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-20*
