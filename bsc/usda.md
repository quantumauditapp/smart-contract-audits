---
token: USDA
ticker: USDA
network: bsc
risk_score: 8
status: low
date: 2026-10-10
---

# USDA (USDA) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 8/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/usda-bsc)

---

## Audit Summary

The USDAWithPremium contract is an ERC-20 token with additional features like access control, blacklisting, and configurable swap taxes. The audit identified two medium-severity issues related to centralized control: the ability for privileged roles to mint new tokens and to modify transfer fees. These controls introduce economic risks for token holders.

> **Final Recommendation:** It is crucial to carefully manage the addresses assigned to privileged roles, especially those with the ability to mint tokens or alter fees. Implement robust multi-signature controls for these roles to prevent single points of failure and enhance security. Ensure transparency regarding any changes to token parameters, such as minting events or fee adjustments, to maintain token holder trust.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The USDAWithPremium contract implements the ERC-20 standard and extends it with AccessControl for managing privileged operations. Key security features include a blacklist mechanism enforced in… |
| **Governance / Economics** | 9/10 | Low | The economic model of the USDAWithPremium token is significantly influenced by centralized control. The ability of a privileged `role` or `vault` to `mint` new tokens (CP-01) can lead to token… |
| **Upgrades** | 10/10 | Low | The USDAWithPremium contract is not deployed as a proxy, meaning it is not designed to be upgradeable. This eliminates risks associated with upgrade mechanisms, such as proxy misconfigurations or… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Locked** | 2.2% — PinkLock02 |
| **Top-1 Unlocked Holder** | ⚠️ 77.8% |
| **Top-3 Unlocked** | ⚠️ 97.9% |

## Security Findings

_⚪ 6 Informational_

### `CP-01` — A privileged address can mint new tokens  *(Severity: Informational · Status: Unresolved)*

A privileged function increases the total supply, diluting every holder. Functions: mint(address,uint256). Restricted to: role, vault.

**Recommendation:** Check who holds these functions and whether a timelock or multisig stands between them and holders.


### `CP-07` — A privileged address can change the transfer fee  *(Severity: Informational · Status: Unresolved)*

The fee taken from transfers is a setting a privileged function can change. Functions: setSwapTaxRatio. Restricted to: defaultadmin, role.

**Recommendation:** Check who holds these functions and whether a timelock or multisig stands between them and holders.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 77.7% of supply. Of that, 6.3% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 64.9% in wallets, 6.5% in other contracts. 398,785 holders in total. For a verified reference asset the largest holders are custodians, exchanges and bridges; concentration is reported, not scored.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as USDA (USDA), market cap $87M, rank #324. 398,785 holders. Verified by: CoinGecko.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $17.3M (DexScreener, all pools). 24h trading volume $8.4M (CoinGecko, all markets, daily snapshot). 24h trading volume $12.4M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Stablecoin  *(Severity: Informational · Status: Acknowledged)*

A token designed to hold a fixed value (usually $1). Its safety rests on what backs it and on who can mint, freeze or pause it. Scored as an established reference asset: its identity is verified, so the issuer's or protocol's controls (listed as findings) are real and are priced once as counterparty risk, and LP locks and holder concentration are not scored — its pools belong to market makers and its largest holders are exchanges, bridges and custody. Basis: CoinGecko category: Stablecoins. Tokenomics — Supply: issued and redeemed by the issuer against its backing. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $17.3M of DEX liquidity across 9 pools. Launch: 428 days of market history.

**Recommendation:** Check what backs the peg and who controls supply: reserve attestations for an issuer-backed coin, collateral and governance for a protocol coin.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x17ea...70ee`](https://bscscan.com/address/0x17eafd08994305d8ace37efb82f1523177ec70ee) |
| **Network** | BNB Chain |
| **Price** | $0.9951 |
| **24h Volume** | $8.18M |
| **Liquidity** | $10.92M |
| **Volume / Liquidity** | 0.7× |
| **Token Age** | 1y |
| **Top-10 Holders** | 77.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 4878 buys / 1810 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xde66f1b24002c1d743ad1ef13cd4b2474295a6f6)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/usda-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-10*
