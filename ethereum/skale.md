---
token: SKALE
ticker: SKL
network: ethereum
risk_score: 39
status: medium
date: 2026-10-09
---

# SKALE (SKL) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 39/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/skale-eth)

---

## Audit Summary

The SkaleToken contract implements an ERC777 token with robust access control and upgradeability features. The audit identified two medium-severity issues stemming from centralized control: a privileged role can mint new tokens, potentially diluting existing holders, and the same role can control a switch that affects token transfers, impacting liquidity and user autonomy. These findings highlight significant centralized power over the token's supply and transferability.

> **Final Recommendation:** To enhance the security and decentralization of the SkaleToken, it is recommended to implement stronger governance mechanisms for critical administrative functions. Specifically, consider introducing multi-signature wallet requirements or time-locks for actions such as minting new tokens and modifying transfer controls. Transparently communicate the scope and limitations of these administrative powers to the community to build trust and mitigate potential economic risks.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The SkaleToken contract is built on the ERC777 standard, incorporating `ReentrancyGuard` for common attack prevention and `AccessControlUpgradeSafe` for robust role-based permissions (7.2 Code… |
| **Governance / Economics** | 1/10 | High | The economic model of the SkaleToken is subject to significant centralized influence (7.4 Economic). A privileged role has the ability to mint new tokens, which can dilute the value for existing… |
| **Upgrades** | 3/10 | High | The contract is designed with upgradeability in mind, inheriting `Initializable` and `AccessControlUpgradeSafe` (7.7 Upgrades). This design allows for future enhancements, bug fixes, or parameter… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 59.5% |
| **Top-3 Unlocked** | ⚠️ 99.6% |

## Security Findings

_🟡 4 Medium · ⚪ 3 Informational_

### `CP-01` — Centralized Control Over Token Supply  *(Severity: Medium · Status: Unresolved)*

A specific role has the ability to call the `mint` function, which creates new SkaleTokens and adds them to the total supply. This means that the controller of this role can increase the total number of tokens at any time, potentially diluting the value of existing tokens held by others.

**Recommendation:** Consider implementing a decentralized governance mechanism or a time-lock for the `mint` function to provide transparency and allow token holders to react to or approve such significant changes to the token supply. Clearly document the conditions under which new tokens can be minted.


### `CP-05` — Centralized Control Over Token Transfers  *(Severity: Medium · Status: Unresolved)*

The `mint` function, controlled by a specific role, can also change an internal `_status` variable. This `_status` variable is checked in the token's transfer path, meaning the controller of this role can effectively enable or disable token transfers or sales at will. This could halt trading and prevent users from moving their tokens.

**Recommendation:** Evaluate the necessity of this transfer control mechanism. If essential, implement a multi-signature wallet or a time-lock for changes to this setting. Ensure that any such control is transparently communicated to token holders, along with the conditions under which it might be activated.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 5 address(es) other than the owner/deployer. One of them — a wallet, 0x858d…34c5 — holds 59.5% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them. This assessment covers the main pool, which holds 61% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Medium · Status: Acknowledged)*

Liquidity $133K (DexScreener, all pools). 24h trading volume $73.9M (CoinGecko, all markets, daily snapshot). 24h trading volume $345K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $1.22 on 2021-03-11; the price is now 99.5874% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 42.3% of supply. What remains: 36.2% in wallets, 6.1% in other contracts. 31,417 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as SKALE (SKL), market cap $31M, rank #674. Traded on Binance, Coinbase. 31,417 holders. Verified by: CoinGecko, exchange listings.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $133K of DEX liquidity across 4 pools. Launch: 2138 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x00c8...a7a7`](https://etherscan.io/address/0x00c83aecc790e8a4453e5dd3b0b4b3680501a7a7) |
| **Network** | Ethereum |
| **Price** | $0.004882 |
| **24h Volume** | $339.0K |
| **Liquidity** | $81.5K |
| **Volume / Liquidity** | 4.2× |
| **Token Age** | 5y |
| **Top-10 Holders** | 42.3% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 182 buys / 240 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0xea631cdaf5033944c5c7b2982fe7626e8e6d12f6368652b1731936009388a4c6)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/skale-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-09*
