---
token: Staked USDai
ticker: SUSDAI
network: arbitrum
risk_score: 10
status: low
date: 2026-10-22
---

# Staked USDai (SUSDAI) — Smart Contract Security Analysis | Arbitrum

> **Risk Score: 10/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/staked-usdai-arb)

---

## Audit Summary

The StakedUSDai protocol is a complex ERC-4626 vault implementation integrated with a loan router system. The architecture relies on a robust role-based access control system and utilizes standard OpenZeppelin upgradeable patterns. No critical or high-severity vulnerabilities were identified during the static analysis of the provided codebase.

> **Final Recommendation:** The protocol demonstrates a strong security posture. It is recommended to maintain the current practice of using multi-signature wallets or timelocks for all administrative roles to prevent single points of failure. 

Continue monitoring the integration with external loan routers, as these represent the primary external attack surface. Ensure that any future changes to the `STRATEGY_ADMIN_ROLE` are audited thoroughly due to the high level of control this role exerts over fund movements.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 9/10 | Low | The architecture follows standard ERC-4626 patterns with additional hooks for loan management. 7.1 Architecture is modular, separating state storage from logic. 7.2 Code Security is high, utilizing… |
| **Governance / Economics** | 9/10 | Low | 7.4 Economic and 7.5 Governance aspects are managed through a Timelock-controlled ProxyAdmin. 7.6 External dependencies are limited to trusted loan routers and standard ERC-20 interfaces. The system… |
| **Upgrades** | 6/10 | Medium | 7.7 Upgrades are handled via a Transparent Proxy pattern with a 48-hour Timelock delay. 7.8 Operations are supported by a robust pause mechanism for emergency scenarios. The upgrade process is… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Transparent |
| **Admin** | OZ ProxyAdmin → Timelock |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | ⚠️ 2 |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_⚪ 6 Informational_

### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 86.7% of supply. What remains: 43.2% in wallets, 43.5% in other contracts. 3,782 holders in total. For a verified reference asset the largest holders are custodians, exchanges and bridges; concentration is reported, not scored.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Staked USDai (SUSDAI), market cap $450M. 3,782 holders. Verified by: CoinGecko.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $268K (DexScreener, all pools). 24h trading volume $2.0M (CoinGecko, all markets, daily snapshot). 24h trading volume $1.3M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-POWERS` — What the token's controller can do  *(Severity: Informational · Status: Acknowledged)*

The contract lets its controller — an owner that could not be resolved — mint new supply; pause all transfers. These are the issuer's controls by design; for a verified issuer they are counterparty risk — the issuer can act on any holder, including you.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-PROFILE` — Asset class: Liquid staking token  *(Severity: Informational · Status: Acknowledged)*

A receipt for staked native tokens that keeps earning staking rewards. Its value depends on the staking protocol and its validators. Scored as an established reference asset: its identity is verified, so the issuer's or protocol's controls (listed as findings) are real and are priced once as counterparty risk, and LP locks and holder concentration are not scored — its pools belong to market makers and its largest holders are exchanges, bridges and custody. Its name presents it as a stable-value coin, yet it trades at $1.11 — it does not hold a peg. Basis: CoinGecko category: Liquid Staking Tokens. Tokenomics — Supply: mintable with no on-chain cap found. Control: an owner that could not be resolved. Code: upgradeable proxy. Fees: no buy or sell tax. Market: $268K of DEX liquidity across 1 pools. Launch: 365 days of market history.

**Recommendation:** Check the staking protocol's validator set, withdrawal queue and governance.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x0b2b...5ef9`](https://arbiscan.io/address/0x0b2b2b2076d95dda7817e785989fe353fe955ef9) |
| **Network** | Arbitrum |
| **Price** | $1.1100 |
| **24h Volume** | $1.33M |
| **Liquidity** | $267.9K |
| **Volume / Liquidity** | 5.0× |
| **Token Age** | 1y |
| **Top-10 Holders** | 86.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 56 buys / 78 sells |

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

- [View on DexScreener](https://dexscreener.com/arbitrum/0x319d28ce8f1aea7b284a8fe2002f4330109b5dc8)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/staked-usdai-arb)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-22*
