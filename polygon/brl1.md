---
token: BRL1
ticker: BRL1
network: polygon
risk_score: 80
status: high
date: 2026-10-26
---

# BRL1 (BRL1) — Smart Contract Security Analysis | Polygon

> **Risk Score: 80/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/brl1-poly)

---

## Audit Summary

The ERC20F contract is a highly privileged, upgradeable token implementation. It features extensive administrative control over token transfers, supply, and user balances. While the code follows standard OpenZeppelin upgradeable patterns, the centralization of power poses significant risks to token holders.

> **Final Recommendation:** It is strongly recommended to implement a multi-signature wallet or a decentralized governance DAO to manage the administrative roles. This would mitigate the risk of a single compromised key causing catastrophic loss of funds or unauthorized token manipulation.

Furthermore, consider adding a time-lock mechanism for all critical administrative functions, including contract upgrades and AccessRegistry changes. This provides the community with a window to react to potentially harmful changes.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The architecture utilizes UUPS proxy patterns for upgradeability and integrates multiple modular components like AccessRegistry and Pause. 7.1 Architecture: Modular design with clear separation of… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic: The protocol allows for arbitrary minting and balance manipulation, which directly impacts token value and holder trust. 7.5 Governance: Administrative roles are centralized, lacking… |
| **Upgrades** | 1/10 | High | 7.7 Upgrades: The contract employs UUPS proxy patterns, which is the industry standard for upgradeable contracts. Upgrades are restricted to authorized roles, ensuring that only the protocol owner… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Uups |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 99.9% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 2 High · 🟡 2 Medium · ⚪ 4 Informational_

### `CP-02` — Administrative Balance Manipulation  *(Severity: High · Status: Unresolved)*

The recoverTokens(address,uint256) function allows privileged roles to move tokens from any user's wallet to the controller's address, effectively bypassing standard ownership.

**Recommendation:** Restrict this function to only recover tokens sent to the contract address itself, rather than allowing arbitrary withdrawal from user wallets.


### `CP-03` — External Dependency Hijacking  *(Severity: High · Status: Unresolved)*

The accessRegistryUpdate(address) function allows an admin to change the logic contract that governs all token transfers, potentially freezing or stealing funds.

**Recommendation:** Implement a time-lock on this function and ensure the registry contract is immutable or governed by a multi-sig.


### `CP-01` — Centralized Minting Authority  *(Severity: Medium · Status: Unresolved)*

The mint(address,uint256) function allows privileged roles to create new tokens at will, which can dilute the value of existing holdings.

**Recommendation:** Implement a hard cap on the total supply or require a governance vote for any minting operations.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 2 address(es) other than the owner/deployer. One of them — a contract, 0x3d54…6381 — holds 99.9% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 96.0% of supply. Of that, 2.7% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 89.2% in wallets, 4.1% in other contracts. 462 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as BRL1 (BRL1), market cap $3M, rank #1971. 462 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $98K (DexScreener, all pools). 24h trading volume $993K (CoinGecko, all markets, daily snapshot). 24h trading volume $56K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Stablecoin — backing unverified  *(Severity: Informational · Status: Acknowledged)*

A token designed to hold a fixed value (usually $1). Its safety rests on what backs it and on who can mint, freeze or pause it. Its identity is not independently verified, so it gets none of the allowances an established stablecoin gets: every power its owner holds over supply and transfers is scored in full, because a peg is only as good as whoever can mint. Basis: CoinGecko category: Stablecoins. Tokenomics — Supply: mintable with no on-chain cap found. Control: an owner that could not be resolved. Code: upgradeable proxy. Fees: no buy or sell tax. Market: $98K of DEX liquidity across 3 pools. Launch: 586 days of market history.

**Recommendation:** Check what backs the peg and who controls supply: reserve attestations for an issuer-backed coin, collateral and governance for a protocol coin.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x5c06...40b5`](https://polygonscan.com/address/0x5c067c80c00ecd2345b05e83a3e758ef799c40b5) |
| **Network** | Polygon |
| **Price** | $0.1857 |
| **24h Volume** | $53.6K |
| **Liquidity** | $98.3K |
| **Volume / Liquidity** | 0.5× |
| **Token Age** | 1y |
| **Top-10 Holders** | 96.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 50 buys / 53 sells |

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

- [View on DexScreener](https://dexscreener.com/polygon/0x27e7f31262733bbbc5255d07d646184fd199bd34)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/brl1-poly)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-26*
