---
token: Immutable X
ticker: IMX
network: ethereum
risk_score: 33
status: low
date: 2026-10-10
---

# Immutable X (IMX) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 33/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/immutable-x-eth)

---

## Audit Summary

The IMXToken contract is an ERC-20 compliant token that incorporates OpenZeppelin's AccessControl for managing administrative functions. A key finding highlights the presence of a minting capability, restricted to a specific role, which allows for the creation of new tokens and could impact the token's economic stability if not managed transparently.

> **Final Recommendation:** It is crucial to establish clear policies and transparent communication regarding the use of the `mint` function and the management of the `MINTER_ROLE`. Consider implementing a multi-signature wallet for the `MINTER_ROLE` to distribute control and enhance security. Regularly audit the addresses holding administrative roles to ensure only authorized entities retain these critical permissions.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The IMXToken contract implements the ERC-20 standard with additional AccessControl features, ensuring standard token functionalities like `transfer` and `approve` are present (7.2 Code Security). The… |
| **Governance / Economics** | 2/10 | High | The economic model of the IMXToken includes a minting capability, controlled by a specific role (7.4 Economic). This allows for the expansion of the token supply, which could impact token value… |
| **Upgrades** | 3/10 | High | The IMXToken contract is not deployed as a proxy (7.7 Upgrades), meaning its logic cannot be directly upgraded or modified after deployment. This eliminates upgrade-related risks such as proxy… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 95.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 2 Medium · ⚪ 4 Informational_

### `CP-01` — Privileged Minting Capability  *(Severity: Medium · Status: Unresolved)*

The `mint` function allows a controller with the `MINTER_ROLE` to create new IMX tokens and add them to any address. This increases the total supply of tokens, which can dilute the value of existing tokens held by other users.

**Recommendation:** Token holders should understand that a specific role has the power to increase the token supply. It is recommended that the project clearly communicates the policies and conditions under which new tokens will be minted. Consider implementing a multi-signature wallet for the `MINTER_ROLE` to prevent a single point of failure.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 3 address(es) other than the owner/deployer. One of them — a wallet, 0x858d…34c5 — holds 95.1% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them. This assessment covers the main pool, which holds 67% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 71.8% of supply. What remains: 8.8% in wallets, 63.0% in other contracts. 96,823 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Immutable (IMX), market cap $186M, rank #196. Traded on Binance, Coinbase. 96,823 holders. Verified by: CoinGecko, exchange listings.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $254K (DexScreener, all pools). 24h trading volume $19.5M (CoinGecko, all markets, daily snapshot). 24h trading volume $103K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $9.52 on 2021-11-25; the price is now 97.8434% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $254K of DEX liquidity across 11 pools. Launch: 1799 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xf57e...79ff`](https://etherscan.io/address/0xf57e7e7c23978c3caec3c3548e3d615c346e79ff) |
| **Network** | Ethereum |
| **Price** | $0.1973 |
| **24h Volume** | $95.4K |
| **Liquidity** | $170.5K |
| **Volume / Liquidity** | 0.6× |
| **Token Age** | 4y |
| **Top-10 Holders** | 71.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 80 buys / 76 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0xfd76be67fff3bac84e3d5444167bbc018f5968b6)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/immutable-x-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-10*
