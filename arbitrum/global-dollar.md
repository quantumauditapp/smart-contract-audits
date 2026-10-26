---
token: Global Dollar
ticker: USDG
network: arbitrum
risk_score: 35
status: medium
date: 2026-10-26
---

# Global Dollar (USDG) — Smart Contract Security Analysis | Arbitrum

> **Risk Score: 35/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/global-dollar-arb)

---

## Audit Summary

The USDG token is a complex, upgradeable ERC-20 implementation utilizing UUPS proxy patterns and extensive role-based access control. While the architecture follows standard industry practices for upgradeability, the presence of uninitialized state variables and centralized minting capabilities introduces significant operational and economic risks. The protocol relies on a Timelock for administrative actions, which provides a necessary buffer for governance decisions.

> **Final Recommendation:** Immediate remediation of the uninitialized state variables is required to prevent potential runtime failures in reward calculation functions. It is recommended to implement a comprehensive initialization check in the constructor or initializer to ensure all state variables are set to expected default values before the contract becomes operational.

Furthermore, consider implementing a hard cap on the total supply or a multi-signature requirement for the minting functions to mitigate the risks associated with centralized supply control. Regular monitoring of the Timelock queue is advised to ensure transparency for all administrative actions.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The architecture utilizes a robust UUPS proxy pattern, ensuring clear separation between logic and storage. Code security is generally high, with standard ERC-20 compliance and well-defined access… |
| **Governance / Economics** | 8/10 | Low | Economic control is centralized, allowing privileged roles to mint or burn tokens at will, which directly impacts token holder value. Governance is managed via a Timelock, providing a 24-hour delay… |
| **Upgrades** | 5/10 | Medium | The UUPS upgrade mechanism is correctly implemented with appropriate access restrictions. Upgrades are gated by the DEFAULT_ADMIN_ROLE, which is further protected by a Timelock. This ensures that any… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Uups |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 50.3% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · ⚪ 6 Informational_

### `CD-01` — Uninitialized State Variables  *(Severity: High · Status: Unresolved)*

Several critical functions, including _getMultiplierAtTime and _isAuthorizedAsClaimer, rely on state variables that are never initialized. This can lead to logic errors or transaction reverts when these functions are invoked.

**Recommendation:** Ensure all state variables are explicitly initialized within the contract constructor or the initialize function before they are accessed by any logic.


### `CP-01` — Centralized Minting Capability  *(Severity: Informational · Status: Unresolved)*

Privileged addresses possess the authority to increase or decrease the total token supply via increaseSupply and decreaseSupply functions. This allows for arbitrary dilution of existing token holders.

**Recommendation:** Implement a supply cap or require multi-signature approval for any supply adjustments to prevent unauthorized or excessive minting.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 91.4% of supply. What remains: 0.0% in wallets, 91.4% in other contracts. 411 holders in total. For a verified reference asset the largest holders are custodians, exchanges and bridges; concentration is reported, not scored.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Global Dollar (USDG), market cap $3.1B, rank #34. 411 holders. Verified by: CoinGecko.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $543K (DexScreener, all pools). 24h trading volume $388.2M (CoinGecko, all markets, daily snapshot). 24h trading volume $918K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Stablecoin — issuer-backed (fiat reserves)  *(Severity: Informational · Status: Acknowledged)*

A token designed to hold a fixed value (usually $1). Its safety rests on what backs it and on who can mint, freeze or pause it. Scored as an established reference asset: its identity is verified, so the issuer's or protocol's controls (listed as findings) are real and are priced once as counterparty risk, and LP locks and holder concentration are not scored — its pools belong to market makers and its largest holders are exchanges, bridges and custody. Basis: CoinGecko category: Fiat-backed Stablecoin. Tokenomics — Supply: issued and redeemed by the issuer against its backing. Control: a timelock with a 24h delay. Code: upgradeable proxy. Fees: no buy or sell tax. Market: $543K of DEX liquidity across 7 pools. Launch: 17 days of market history.

**Recommendation:** Check what backs the peg and who controls supply: reserve attestations for an issuer-backed coin, collateral and governance for a protocol coin.


### `QA-RECENT` — Recently launched — 17 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 17 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x004b...9bbc`](https://arbiscan.io/address/0x004b506865409877c9fa29bfb1eba929984b9bbc) |
| **Network** | Arbitrum |
| **Price** | $1.0012 |
| **24h Volume** | $529.4K |
| **Liquidity** | $234.5K |
| **Volume / Liquidity** | 2.3× |
| **Token Age** | 17d |
| **Top-10 Holders** | 91.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 210 buys / 129 sells |

## Security Flags (1/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Sources

- [View on DexScreener](https://dexscreener.com/arbitrum/0x09328be718d89228a985471bb470988a34d0b162)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/global-dollar-arb)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-26*
