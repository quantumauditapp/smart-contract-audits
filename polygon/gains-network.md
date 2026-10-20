---
token: Gains Network
ticker: GNS
network: polygon
risk_score: 51
status: medium
date: 2026-10-20
---

# Gains Network (GNS) — Smart Contract Security Analysis | Polygon

> **Risk Score: 51/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/gains-network-poly)

---

## Audit Summary

The GainsNetworkToken is a standard ERC-20 implementation with additional minting and role-based access control capabilities. The architecture relies on OpenZeppelin's AccessControl for administrative operations. While the core token logic is standard, the contract contains a design flaw regarding trapped ETH and centralized minting authority. 7.1 Architecture: Standard ERC-20 with role-based minting. 7.2 Code Security: Standard library usage. 7.3 Access Control: Robust role-based system. 7.4 Economic: Centralized minting risk. 7.5 Governance: Admin-controlled grant requests. 7.6 External: Standard meta-transaction support. 7.7 Upgrades: Not applicable. 7.8 Operations: ETH stuck in contract.

> **Final Recommendation:** Implement a recovery function restricted to the owner to withdraw any ETH accidentally sent to the contract address. Ensure that the addresses holding the MINTER_ROLE and DEPOSITOR_ROLE are secured via multi-signature wallets to mitigate the impact of a single compromised key.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes well-audited OpenZeppelin libraries for ERC-20 and AccessControl functionality. The code is clean and follows standard patterns for meta-transactions. However, the contract… |
| **Governance / Economics** | 1/10 | High | The protocol grants significant power to the MINTER_ROLE, allowing for arbitrary supply expansion. While this is intended for cross-chain bridging via the DEPOSITOR_ROLE, it presents a centralization… |
| **Upgrades** | 2/10 | High | The contract is not upgradeable and does not utilize proxy patterns. This ensures immutability of the logic, though it prevents patching of the identified ETH recovery issue. The current state is… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 85.5% |
| **Top-3 Unlocked** | ⚠️ 91.0% |

## Security Findings

_🟡 3 Medium · ⚪ 4 Informational_

### `CD-01` — ETH Trapped in Contract  *(Severity: Medium · Status: Unresolved)*

The contract can receive ETH through meta-transactions or direct transfers, but it lacks any function to withdraw or transfer these funds out. Any ETH sent to the contract address will be permanently locked.

**Recommendation:** Add a function that allows the contract owner to withdraw any ETH balance held by the contract.


### `CP-01` — Centralized Minting Authority  *(Severity: Medium · Status: Unresolved)*

The functions mint, deposit, and withdraw allow privileged addresses to increase the total token supply at will. This creates a risk where a compromised admin key could dilute the value of all existing tokens.

**Recommendation:** Restrict the minting authority to a multi-signature wallet or a time-locked governance contract to prevent unauthorized supply inflation.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 98.5% is held, unlocked, by 10 address(es) other than the owner/deployer. One of them — a contract, 0x3302…4e43 — holds 85.5% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them. This assessment covers the main pool, which holds 44% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 74.2% of supply. Of that, 2.1% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 61.7% in wallets, 10.3% in other contracts. 20,670 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Gains (GAINS), market cap $10M, rank #1241. Traded on Binance. 20,670 holders. Verified by: exchange listings.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $104K (DexScreener, all pools). 24h trading volume $1.1M (CoinGecko, all markets, daily snapshot). 24h trading volume $134K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $12.48 on 2023-02-16; the price is now 96.8138% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $104K of DEX liquidity across 30 pools. Launch: 1819 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xe541...7896`](https://polygonscan.com/address/0xe5417af564e4bfda1c483642db72007871397896) |
| **Network** | Polygon |
| **Price** | $0.4896 |
| **24h Volume** | $30.8K |
| **Liquidity** | $46.3K |
| **Volume / Liquidity** | 0.7× |
| **Token Age** | 5y |
| **Top-10 Holders** | 74.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 352 buys / 377 sells |

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

- [View on DexScreener](https://dexscreener.com/polygon/0x6e53cb6942e518376e9e763554db1a45ddcd25c4)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/gains-network-poly)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-20*
