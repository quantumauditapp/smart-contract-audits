---
token: GMX
ticker: GMX
network: arbitrum
risk_score: 41
status: medium
date: 2026-10-28
---

# GMX (GMX) — Smart Contract Security Analysis | Arbitrum

> **Risk Score: 41/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/gmx-arb)

---

## Audit Summary

The GMX token contract is a highly privileged, upgradeable-style ERC-20 implementation. It features complex reward tracking and administrative controls that allow for minting, fee adjustments, and transfer restrictions. While the code is well-structured, the high degree of centralization poses a significant risk to token holders.

> **Final Recommendation:** Token holders should monitor governance actions closely, as the 'gov' role has broad authority over token supply and transferability. It is recommended to transition these privileged functions to a multi-signature wallet or a decentralized DAO structure to mitigate single-point-of-failure risks.

Ensure that all administrative addresses are secured with hardware security modules or multi-party computation (MPC) to prevent unauthorized access to the 'mint' and 'setInPrivateTransferMode' functions.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract implements standard ERC-20 functionality with robust internal reward tracking. 7.1 Architecture is modular, separating minting and administrative logic. 7.2 Code Security is high… |
| **Governance / Economics** | 2/10 | High | 7.4 Economic and 7.5 Governance aspects are heavily centralized under the 'gov' and 'admin' roles. These roles have the power to mint tokens, modify transfer rules, and withdraw assets. This design… |
| **Upgrades** | 3/10 | High | 7.7 Upgrades are not implemented via proxy patterns in this specific contract. However, 7.8 Operations are highly flexible due to the extensive administrative functions. This allows for protocol… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | 37.5% |
| **Top-3 Unlocked** | 66.0% |

## Security Findings

_🟡 4 Medium · ⚪ 4 Informational_

### `CP-01` — Centralized Minting Authority  *(Severity: Medium · Status: Unresolved)*

The 'mint' function allows privileged addresses to create new tokens, which can dilute the holdings of existing users. This is restricted to addresses designated as minters by the governance role.

**Recommendation:** Implement a time-lock on the minting function or require a multi-signature approval process for any increase in total supply.


### `CP-05` — Governance Control Over Transferability  *(Severity: Medium · Status: Unresolved)*

The 'setInPrivateTransferMode' function allows the governance role to toggle a switch that can restrict or block token transfers for all users. This creates a risk where liquidity could be frozen by the protocol controllers.

**Recommendation:** Document the specific conditions under which this mode would be activated and consider adding a community-veto mechanism for such drastic changes.


### `CP-07` — Administrative Control Over Transfer Fees  *(Severity: Medium · Status: Unresolved)*

Administrative roles can modify transfer fees and reward logic by changing non-staking account statuses. This allows controllers to influence the economic distribution of the token unilaterally.

**Recommendation:** Establish clear, transparent rules for fee adjustments and ensure these changes are communicated to the community in advance.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 86.0% is held, unlocked, by 10 address(es) other than the owner/deployer. No single one holds a majority: their exits thin the market rather than hand anyone the pool. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them. This assessment covers the main pool, which holds 43% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 80.5% of supply. What remains: 13.4% in wallets, 67.1% in other contracts. 297,575 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as GMX (GMX), market cap $92M, rank #294. Traded on Binance. 297,575 holders. Verified by: CoinGecko, exchange listings.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $587K (DexScreener, all pools). 24h trading volume $4.3M (CoinGecko, all markets, daily snapshot). 24h trading volume $618K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $91.07 on 2023-04-18; the price is now 90.524% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: gov — a contract. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $587K of DEX liquidity across 30 pools. Launch: 1877 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xfc5a...ad0a`](https://arbiscan.io/address/0xfc5a1a6eb076a2c7ad06ed22c90d7e710e35ad0a) |
| **Network** | Arbitrum |
| **Price** | $8.6100 |
| **24h Volume** | $38.7K |
| **Liquidity** | $250.2K |
| **Volume / Liquidity** | 0.2× |
| **Token Age** | 5y |
| **Top-10 Holders** | 80.5% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 295 buys / 123 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/arbitrum/0x0a36952fb8c8dc6daefb2fadb07c5212f560880e)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/gmx-arb)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-28*
