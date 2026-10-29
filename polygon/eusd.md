---
token: eUSD
ticker: EUSD
network: polygon
risk_score: 69
status: high
date: 2026-10-29
---

# eUSD (EUSD) — Smart Contract Security Analysis | Polygon

> **Risk Score: 69/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/eusd-poly)

---

## Audit Summary

The protocol implements a standard upgradeable stablecoin with robust access control and blacklist capabilities. The architecture relies on OpenZeppelin's upgradeable patterns, ensuring standard compliance. While the system is well-structured, the presence of state shadowing requires attention to prevent logic errors during future upgrades.

> **Final Recommendation:** The protocol should prioritize the resolution of the identified state shadowing issue to ensure storage integrity across future upgrades. It is recommended to implement a multi-signature wallet for all privileged roles to prevent single points of failure in administrative actions.

Regular audits of the Beacon implementation are advised whenever logic changes are introduced. Ensure that all role-granting processes are documented and audited to maintain the integrity of the access control system.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The architecture utilizes a modular approach with clear separation of concerns via AccessControl. 7.1 Architecture is sound, leveraging standard proxy patterns. 7.2 Code Security is high, though 7.3… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic and 7.5 Governance risks are centralized under the admin roles. The ability to mint and blacklist provides necessary operational control but introduces significant trust requirements.… |
| **Upgrades** | 2/10 | High | 7.7 Upgrades are managed via a Beacon Proxy pattern, allowing for centralized implementation updates. This provides high flexibility but necessitates rigorous testing of storage layouts. The… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 2 High · 🟡 1 Medium · ⚪ 4 Informational_

### `CD-01` — State Variable Shadowing  *(Severity: High · Status: Unresolved)*

The contract contains state variables that shadow inherited variables, which can lead to unexpected behavior when accessing storage slots. This occurs when a child contract declares a variable with the same name as one in a parent contract, potentially causing the wrong value to be read or written during execution.

**Recommendation:** Rename the shadowed state variables in the child contract to ensure they are distinct from those in the inherited contracts. Verify the storage layout after the changes to ensure compatibility with the existing proxy state.


### `QA-POWERS` — What the token's controller can do  *(Severity: High · Status: Acknowledged)*

The contract lets its controller — an owner that could not be resolved — mint new supply; freeze or blacklist individual addresses; pause all transfers. Nothing independent vouches for whoever holds them, so each is a live risk to holders.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a contract, 0xd623…ea20 — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them. This assessment covers the main pool, which holds 84% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 98.6% of supply. What remains: 0.3% in wallets, 98.3% in other contracts. 337 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as eUSD (EUSD), market cap $10M, rank #1260. 337 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $1.2M (GeckoTerminal, all pools). 24h trading volume $1.2M (CoinGecko, all markets, daily snapshot). 24h trading volume $148K (GeckoTerminal, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Stablecoin — backing unverified  *(Severity: Informational · Status: Acknowledged)*

A token designed to hold a fixed value (usually $1). Its safety rests on what backs it and on who can mint, freeze or pause it. Its identity is not independently verified, so it gets none of the allowances an established stablecoin gets: every power its owner holds over supply and transfers is scored in full, because a peg is only as good as whoever can mint. Basis: CoinGecko category: Stablecoins. Tokenomics — Supply: mintable with no on-chain cap found. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $1.2M of DEX liquidity across 5 pools. Launch: 288 days of market history.

**Recommendation:** Check what backs the peg and who controls supply: reserve attestations for an issuer-backed coin, collateral and governance for a protocol coin.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x1491...2949`](https://polygonscan.com/address/0x14913815bcfde78baead2111f463d038ac9c2949) |
| **Network** | Polygon |
| **Price** | $0.99774127 |
| **24h Volume** | $62.8K |
| **Liquidity** | $1.00M |
| **Volume / Liquidity** | 0.1× |
| **Token Age** | 9mo |
| **Top-10 Holders** | 98.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 106 buys / 150 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/polygon/0x14913815bcfde78baead2111f463d038ac9c2949)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/eusd-poly)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-29*
