---
token: Liquid staked Ether 2.0
ticker: STETH
network: ethereum
risk_score: 38
status: medium
date: 2026-10-01
---

# Liquid staked Ether 2.0 (STETH) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 38/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/liquid-staked-ether-20-eth)

---

## Audit Summary

The Lido contract, an ERC-20 token implementation, manages staked ETH and associated operations. It features extensive access control and upgradeability. The audit identified two high-severity issues related to privileged balance manipulation and a technical inconsistency with `msg.value` handling in an internal function. These findings highlight the significant power held by privileged roles within the protocol.

> **Final Recommendation:** It is crucial to implement stringent security measures around the privileged roles that control the Lido contract, especially those with the ability to directly manipulate user balances or critical staking parameters. A multi-signature wallet should ideally secure these roles, and all administrative actions should follow a transparent governance process. Furthermore, a thorough review of the `_submit` function's payable status and its interaction with `msg.value` is recommended to ensure consistent and expected behavior, preventing potential reverts or unexpected state changes.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The Lido contract is an ERC-20 token with rebasing shares, inheriting from `ReentrancyGuard` for security. It includes numerous privileged functions controlled by specific roles, enabling… |
| **Governance / Economics** | 8/10 | Low | The contract implements a robust access control system using AragonApp's ACL, assigning specific roles for critical operations. This centralized control allows for comprehensive management of staking… |
| **Upgrades** | 5/10 | Medium | The Lido contract is deployed as an upgradeable proxy using a custom Etherscan-detected pattern. This design allows for future modifications and enhancements to the contract logic without requiring a… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Etherscan Detected Custom |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 98.5% |
| **Top-3 Unlocked** | ⚠️ 99.5% |

## Security Findings

_🟠 1 High · ⚪ 5 Informational_

### `CD-01` — Internal Function Handling Ether Is Not Explicitly Marked Payable  *(Severity: High · Status: Unresolved)*

The internal `_submit` function, which is responsible for processing incoming Ether (msg.value) when users stake, is not explicitly marked as `payable`. While its external callers (`submit` and the `fallback` function) are `payable`, this inconsistency in the internal function's declaration could lead to unexpected reverts if `_submit` were ever called directly or indirectly from a non-payable context while attempting to handle Ether.

**Recommendation:** While the current external callers are `payable`, it is a best practice for internal functions that are intended to receive and process Ether to be explicitly marked `payable`. This ensures clarity and prevents potential issues if the call path changes in future upgrades. Token holders should ensure that the protocol's technical team reviews and addresses this declaration for robustness.


### `CP-02` — Privileged Address Can Directly Change Token Holders' Balances  *(Severity: Informational · Status: Unresolved)*

The contract allows certain privileged addresses to directly modify the token balances (shares) of any user. Functions like `transferShares`, `transferSharesFrom`, `submit`, `mintShares`, and `mintExternalShares` can be called by these privileged roles to move, create, or burn tokens from any account, including those of other token holders. This means a compromised or malicious privileged address could potentially take tokens from users or inflate the supply.

**Recommendation:** Token holders should be aware that the administrators of the Lido contract possess significant control over token balances. It is critical that the keys controlling these privileged addresses are secured with the highest possible standards, such as multi-signature wallets, and that all actions are transparently governed.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 62.9% of supply. What remains: 5.5% in wallets, 57.4% in other contracts. 628,147 holders in total. For a verified reference asset the largest holders are custodians, exchanges and bridges; concentration is reported, not scored.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Lido Staked Ether (STETH), market cap $26.4B. 628,147 holders. Verified by: CoinGecko.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $150.1M (DexScreener, all pools). 24h trading volume $49.2M (CoinGecko, all markets, daily snapshot). 24h trading volume $42.5M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Liquid staking token  *(Severity: Informational · Status: Acknowledged)*

A receipt for staked native tokens that keeps earning staking rewards. Its value depends on the staking protocol and its validators. Scored as an established reference asset: its identity is verified, so the issuer's or protocol's controls (listed as findings) are real and are priced once as counterparty risk, and LP locks and holder concentration are not scored — its pools belong to market makers and its largest holders are exchanges, bridges and custody. Basis: CoinGecko category: Liquid Staking Tokens. Tokenomics — Supply: fixed — the contract has no mint function. Control: an owner that could not be resolved. Code: upgradeable proxy. Fees: no buy or sell tax. Market: $150.1M of DEX liquidity across 11 pools. Launch: 2112 days of market history.

**Recommendation:** Check the staking protocol's validator set, withdrawal queue and governance.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xae7a...fe84`](https://etherscan.io/address/0xae7ab96520de3a18e5e111b5eaab095312d7fe84) |
| **Network** | Ethereum |
| **Price** | $2,686.0035 |
| **24h Volume** | $26.45M |
| **Liquidity** | $104.07M |
| **Volume / Liquidity** | 0.3× |
| **Token Age** | 5y |
| **Top-10 Holders** | 62.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 61 buys / 108 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0xdc24316b9ae028f1497c275eb9192a3ea0f67022)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/liquid-staked-ether-20-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-01*
