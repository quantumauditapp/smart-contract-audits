---
token: GROOVE
ticker: GROOVE
network: base
risk_score: 50
status: medium
date: 2026-09-29
---

# GROOVE (GROOVE) — Smart Contract Security Analysis | Base

> **Risk Score: 50/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/groove-base)

---

## Audit Summary

The GROOVE contract is an ERC-20 token implementation. While the contract's ownership has been renounced, a specific address retains the ability to mint new tokens, which could lead to supply dilution. The core ERC-20 functionalities are standard, and no upgradeability mechanism is present.

> **Final Recommendation:** It is crucial to ensure the `claimedinitialrelease` address, which controls token minting, is secured with robust multi-signature or time-lock mechanisms to prevent unauthorized supply inflation. Consider transparently communicating the minting schedule and total supply limits to the community. Regular monitoring of the `claimedinitialrelease` address's activity is also advised.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The GROOVE contract implements standard ERC-20 token functionalities (7.2 Code Security). Ownership of the contract has been renounced, meaning functions restricted to the owner, such as… |
| **Governance / Economics** | 8/10 | Low | The economic model of the GROOVE token is primarily influenced by the minting capability held by the `claimedinitialrelease` address (7.4 Economic). This address can increase the total supply of… |
| **Upgrades** | 6/10 | Medium | The GROOVE contract is not designed with an upgradeability pattern (7.7 Upgrades). This means the contract's logic cannot be modified after deployment, which eliminates risks associated with proxy… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Locked** | 100.0% — UNCX Locker |
| **Top-1 Unlocked Holder** | 0.0% |

## Security Findings

_🟠 1 High · 🟡 1 Medium · ⚪ 4 Informational_

### `QA-LIQUIDITY` — Liquidity lock has expired  *(Severity: High · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% still sits in UNCX Locker, but that lock expired on 26 May 2026 — its owner can withdraw it at any moment. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `CP-01` — Privileged Address Can Mint New Tokens  *(Severity: Medium · Status: Unresolved)*

The `claimedinitialrelease` address has the ability to create new GROOVE tokens using the `depositAndClaimTokens` and `claimVestedTokens` functions. This means that this specific address can increase the total supply of GROOVE tokens, which could dilute the value of existing tokens held by others.

**Recommendation:** Token holders should be aware that the `claimedinitialrelease` address can mint new tokens. It is recommended that the project team consider implementing a maximum total supply for GROOVE tokens or ensure that the `claimedinitialrelease` address is controlled by a highly secure multi-signature wallet or a time-locked contract to prevent unauthorized or excessive minting.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 42.0% of supply. Of that, 8.3% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 15.9% in wallets, 17.8% in other contracts. 61,903 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as GROOVE (GROOVE). 61,903 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $32K (DexScreener, all pools). 24h trading volume $73K (CoinGecko, all markets, daily snapshot). 24h trading volume $49K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $0.00937 on 2024-06-04; the price is now 97.9869% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $32K of DEX liquidity across 2 pools. Launch: 856 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x1cd3...08d3`](https://basescan.org/address/0x1cd38856ee0fdfd65c757e530e3b1de3061008d3) |
| **Network** | Base |
| **Price** | $0.0002053 |
| **24h Volume** | $49.1K |
| **Liquidity** | $32.2K |
| **Volume / Liquidity** | 1.5× |
| **Token Age** | 2y |
| **Top-10 Holders** | 42.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 277 buys / 196 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/base/0xef0a856b572108ef0ad9dac10580811939ca3bb7)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/groove-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-29*
