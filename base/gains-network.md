---
token: Gains Network
ticker: GNS
network: base
risk_score: 67
status: high
date: 2026-10-14
---

# Gains Network (GNS) — Smart Contract Security Analysis | Base

> **Risk Score: 67/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/gains-network-base)

---

## Audit Summary

This audit covers the GainsNetworkToken contract, an ERC-20 token with role-based access control. The primary finding is a medium-severity issue related to a privileged minting function, which allows a designated role to increase the token supply.

> **Final Recommendation:** Token holders should be fully aware of the centralized control over token supply through the `mint` function. It is recommended to establish clear, transparent policies regarding the use of the `MINTER_ROLE`, including who holds it and under what conditions new tokens can be minted. For enhanced security, consider implementing multi-signature requirements or time-locks for critical administrative actions, especially for the `MINTER_ROLE`, to prevent single points of failure and provide a window for community oversight.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The GainsNetworkToken contract implements the ERC-20 standard, providing standard token functionalities like `transfer` and `balanceOf`. It also includes `AccessControlEnumerable` for managing… |
| **Governance / Economics** | 1/10 | High | The contract utilizes `AccessControlEnumerable` for managing administrative roles, including the `MINTER_ROLE`. This role-based access control centralizes the power to mint new tokens via the `mint`… |
| **Upgrades** | 2/10 | High | The GainsNetworkToken contract is not designed as an upgradeable proxy. Therefore, there are no upgrade-specific risks associated with proxy patterns or implementation changes (7.7 Upgrades). Any… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 99.9% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 2 Medium · ⚪ 4 Informational_

### `CP-01` — Privileged Token Minting Capability  *(Severity: Medium · Status: Unresolved)*

The `mint(address,uint256)` function allows an address with the `MINTER_ROLE` to create new tokens and assign them to any address. This increases the total supply of the token, which can dilute the value of existing token holdings for all token holders.

**Recommendation:** Token holders should be aware that a specific role has the power to mint new tokens. It is crucial to understand who holds the `MINTER_ROLE` and the policies governing its use. Consider implementing a multi-signature wallet for this role or a time-locked mechanism for minting operations to enhance security and transparency.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 2 address(es) other than the owner/deployer. One of them — a contract, 0xc07e…2f3a — holds 99.9% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 92.9% of supply. Of that, 1.0% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 2.0% in wallets, 89.8% in other contracts. 660 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Gains Network (GNS), market cap $18M, rank #918. Traded on Binance. 660 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $27K (DexScreener, all pools). 24h trading volume $18.2M (CoinGecko, all markets, daily snapshot). 24h trading volume $40K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $12.48 on 2023-02-16; the price is now 94.0523% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $27K of DEX liquidity across 4 pools. Launch: 750 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xfb1a...e7ac`](https://basescan.org/address/0xfb1aaba03c31ea98a3eec7591808acb1947ee7ac) |
| **Network** | Base |
| **Price** | $0.6747 |
| **24h Volume** | $40.3K |
| **Liquidity** | $26.9K |
| **Volume / Liquidity** | 1.5× |
| **Token Age** | 2y |
| **Top-10 Holders** | 92.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 576 buys / 422 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0xc1f330e0cf5d35d452c6be1bd28d89ec31dbf462)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/gains-network-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-14*
