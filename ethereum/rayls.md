---
token: Rayls
ticker: RLS
network: ethereum
risk_score: 72
status: high
date: 2026-10-26
---

# Rayls (RLS) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 72/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/rayls-eth)

---

## Audit Summary

The RaylsToken contract is an upgradeable ERC-20 token utilizing the UUPS pattern. While it implements standard OpenZeppelin libraries for access control and pausing, a critical vulnerability exists in the initialization of the implementation contract, which could allow an attacker to take control of the proxy logic. The protocol relies on centralized roles for minting and pausing, which are standard but require secure key management.

> **Final Recommendation:** Immediately initialize the implementation contract upon deployment or add a constructor that calls _disableInitializers() to prevent unauthorized initialization. Ensure that all privileged roles (MINTER_ROLE, PAUSER_ROLE) are assigned to multi-signature wallets or time-locked governance contracts to prevent single-point-of-failure risks.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The architecture follows standard UUPS proxy patterns, ensuring modularity and upgradeability. 7.1 Architecture is sound, utilizing established OpenZeppelin standards for 7.2 Code Security. However… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic parameters are defined by a single minting event, preventing inflation after the initial supply is created. 7.5 Governance is centralized via AccessControl roles, which is appropriate… |
| **Upgrades** | 5/10 | Medium | 7.7 Upgrades are handled via UUPS, which is gas-efficient and secure when implemented correctly. 7.8 Operations are supported by pause/unpause functionality to mitigate emergency risks. The current… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | 34.3% |
| **Top-3 Unlocked** | ⚠️ 86.2% |

## Security Findings

_🔴 1 Critical · 🟡 1 Medium · ⚪ 4 Informational_

### `CD-01` — Unprotected Implementation Contract Initialization  *(Severity: Critical · Status: Unresolved)*

The implementation contract is not initialized upon deployment, allowing any user to call the initialize function. This could allow an attacker to take control of the implementation logic or potentially disrupt the proxy's upgradeability.

**Recommendation:** Add a constructor to the implementation contract that calls _disableInitializers() to ensure the implementation cannot be initialized after deployment.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 4 address(es) other than the owner/deployer. No single one holds a majority: their exits thin the market rather than hand anyone the pool. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them. This assessment covers the main pool, which holds 80% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 63.8% of supply. What remains: 18.7% in wallets, 45.1% in other contracts. 46,483 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Rayls (RLS), market cap $5M, rank #1587. Traded on Coinbase. 46,483 holders. Verified by: exchange listings.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $18K (DexScreener, all pools). 24h trading volume $7.1M (CoinGecko, all markets, daily snapshot). 24h trading volume $43K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $0.0364 on 2025-12-02; the price is now 92.5899% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $18K of DEX liquidity across 3 pools. Launch: 179 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xb5f7...4fbd`](https://etherscan.io/address/0xb5f7b021a78f470d31d762c1dda05ea549904fbd) |
| **Network** | Ethereum |
| **Price** | $0.0024 |
| **24h Volume** | $37.5K |
| **Liquidity** | $14.1K |
| **Volume / Liquidity** | 2.7× |
| **Token Age** | 5mo |
| **Top-10 Holders** | 63.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 195 buys / 126 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x2e3a2d2762c4c1cba48a26185fe4c1483db2ecfaef3e02f5aa48a20de1324ea3)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/rayls-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-26*
