---
token: Orderly Network
ticker: ORDER
network: base
risk_score: 71
status: high
date: 2026-10-24
---

# Orderly Network (ORDER) — Smart Contract Security Analysis | Base

> **Risk Score: 71/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/orderly-network-base)

---

## Audit Summary

The OrderOFT contract implements a cross-chain token bridge using the LayerZero OFT standard. The architecture relies on a UUPS proxy pattern and is managed by a 2-of-3 multisig. The codebase demonstrates high adherence to standard library patterns, though minor rounding risks exist in dust removal logic.

> **Final Recommendation:** The protocol is well-architected and follows secure development practices. We recommend maintaining the multisig threshold and ensuring that any future changes to the 'enforcedOptions' or 'peers' are subject to a rigorous multi-signature review process before execution.

For the identified rounding issue, ensure that the frontend or integration layer accounts for potential dust accumulation during cross-chain transfers to prevent minor balance discrepancies for end-users.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract utilizes a robust modular architecture inheriting from LayerZero's OApp and OFT standards. 7.1 Architecture is well-structured using UUPS proxies for upgradeability. 7.2 Code Security is… |
| **Governance / Economics** | 2/10 | High | 7.3 Access Control is centralized under a 2-of-3 multisig, providing a balance between security and operational agility. 7.4 Economic parameters are governed by the owner, who can pause the contract… |
| **Upgrades** | 2/10 | High | 7.7 Upgrades are handled via the UUPS pattern, which is the industry standard for gas-efficient and secure proxy management. 7.8 Operations are supported by pause/unpause functionality, allowing for… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Uups |
| **Implementation** | ✅ Verified source |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 4 Informational_

### `QA-POWERS` — What the token's controller can do  *(Severity: High · Status: Acknowledged)*

The contract lets its controller — a 2-of-3 multisig — pause all transfers. Nothing independent vouches for whoever holds them, so each is a live risk to holders.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a wallet, 0x647c…c73a — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `CD-01` — Rounding loss in dust removal  *(Severity: Low · Status: Unresolved)*

The _removeDust function performs division before multiplication, which can lead to minor precision loss during token calculations.

**Recommendation:** Reorder operations to perform multiplication before division to maintain maximum precision.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 80.1% of supply. What remains: 11.3% in wallets, 68.8% in other contracts. 4,880 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Orderly (ORDER), market cap $14M, rank #1004. 4,880 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $173K (DexScreener, all pools). 24h trading volume $3.6M (CoinGecko, all markets, daily snapshot). 24h trading volume $1.1M (DexScreener, all pools). CoinGecko's record for this coin: all-time high $0.492 on 2025-10-06; the price is now 92.9981% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: a 2-of-3 multisig. Code: upgradeable proxy. Fees: no buy or sell tax. Market: $173K of DEX liquidity across 8 pools. Launch: 396 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x4e20...97b8`](https://basescan.org/address/0x4e200fe2f3efb977d5fd9c430a41531fb04d97b8) |
| **Network** | Base |
| **Price** | $0.07065 |
| **24h Volume** | $1.15M |
| **Liquidity** | $172.6K |
| **Volume / Liquidity** | 6.7× |
| **Token Age** | 1y |
| **Top-10 Holders** | 80.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 3061 buys / 3375 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Sources

- [View on DexScreener](https://dexscreener.com/base/0x27bd426ec343845995c527d634c4e07f0608aacd)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/orderly-network-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-24*
