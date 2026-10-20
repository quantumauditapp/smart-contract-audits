---
token: Chiliz
ticker: CHZ
network: base
risk_score: 40
status: medium
date: 2026-10-06
---

# Chiliz (CHZ) — Smart Contract Security Analysis | Base

> **Risk Score: 40/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/chiliz-base)

---

## Audit Summary

The Chiliz token contract is an upgradeable ERC-20 token built upon OpenZeppelin's battle-tested libraries, incorporating standard features such as pausing, minting, and burning. It utilizes a UUPS proxy pattern for upgradeability and Access Control for managing privileged roles. This analysis did not identify any specific vulnerabilities.

> **Final Recommendation:** Maintain strict operational security for all private keys associated with the `ADMIN_ROLE`, `MINTER_ROLE`, `PAUSER_ROLE`, and upgrade-related roles. Implement multi-signature wallets for these critical roles to mitigate single points of failure. Regularly review and audit any proposed upgrades before deployment to ensure no new vulnerabilities are introduced.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 7/10 | Low | The contract leverages robust OpenZeppelin libraries for its core ERC-20 functionality, including `ERC20Upgradeable`, `ERC20PausableUpgradeable`, and `ERC20BurnableUpgradeable`. Reentrancy protection… |
| **Governance / Economics** | 1/10 | High | The contract incorporates several centralized control mechanisms managed by specific roles (7.5 Governance). A `MINTER_ROLE` can increase the total supply via `mint(address,uint256)`, and a… |
| **Upgrades** | 1/10 | High | The contract is implemented as an upgradeable UUPS proxy (7.7 Upgrades), allowing its logic to be modified in the future. The `upgradeToAndCall` function is restricted by Access Control, ensuring… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Uups |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 63.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 1 Medium · ⚪ 5 Informational_

### `QA-POWERS` — What the token's controller can do  *(Severity: High · Status: Acknowledged)*

The contract lets its controller — an owner that could not be resolved — mint new supply; pause all transfers. Nothing independent vouches for whoever holds them, so each is a live risk to holders.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 2 address(es) other than the owner/deployer. One of them — a wallet, 0x3662…ba86 — holds 63.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them. This assessment covers the main pool, which holds 76% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 94.9% of supply. What remains: 0.8% in wallets, 94.0% in other contracts. 849 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Chiliz (CHZ), market cap $175M, rank #202. 849 holders. Verified by: CoinGecko.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $336K (DexScreener, all pools). 24h trading volume $16.7M (CoinGecko, all markets, daily snapshot). 24h trading volume $41K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $0.879 on 2021-03-13; the price is now 98.1094% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: an owner that could not be resolved. Code: upgradeable proxy. Fees: no buy or sell tax. Market: $336K of DEX liquidity across 2 pools. Launch: 365 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x70c8...d0a2`](https://basescan.org/address/0x70c8392de9b39a1e48d12a70af6ff4be25d6d0a2) |
| **Network** | Base |
| **Price** | $0.01676 |
| **24h Volume** | $41.0K |
| **Liquidity** | $255.9K |
| **Volume / Liquidity** | 0.2× |
| **Token Age** | 1y |
| **Top-10 Holders** | 94.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 167 buys / 129 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0xa11fbd0f7112f2fad10f92f09b4a8d85e8ddd401)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/chiliz-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-06*
