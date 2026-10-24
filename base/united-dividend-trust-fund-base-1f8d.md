---
token: United Dividend Trust Fund
ticker: UDTF
network: base
risk_score: 57
status: medium
date: 2026-10-24
---

# United Dividend Trust Fund (UDTF) — Smart Contract Security Analysis | Base

> **Risk Score: 57/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/united-dividend-trust-fund-base-1f8d)

---

## Audit Summary

The DERC20 contract is a standard ERC-20 implementation with additional governance, voting, and vesting capabilities. The protocol relies on a centralized owner to manage inflation, token vesting, and transfer restrictions. While the code follows established OpenZeppelin standards, the high degree of administrative control poses a significant centralization risk to token holders.

> **Final Recommendation:** To improve security, the project should transition administrative functions to a multi-signature wallet or a decentralized governance contract to mitigate single-point-of-failure risks. Implementing a timelock on sensitive functions like updateMintRate would provide transparency and allow the community to react to significant economic changes.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The architecture leverages battle-tested OpenZeppelin libraries for ERC-20, voting, and permit functionality. 7.1 Architecture and 7.2 Code Security are robust, utilizing standard patterns for state… |
| **Governance / Economics** | 3/10 | High | 7.4 Economic and 7.5 Governance aspects are heavily centralized. The owner has the ability to mint new tokens via updateMintRate and control market liquidity through lockPool. While inflation is… |
| **Upgrades** | 4/10 | Medium | 7.7 Upgrades are not supported as the contract is not a proxy. 7.8 Operations are straightforward, relying on the owner to trigger vesting releases and pool updates. The absence of upgradeability… |

## Security Findings

_🟡 2 Medium · ⚪ 5 Informational_

### `CP-01` — Centralized Minting Authority  *(Severity: Medium · Status: Unresolved)*

The owner can call updateMintRate and release to increase the total supply of tokens. This allows the owner to dilute existing token holders at their discretion, provided the annual inflation cap is respected.

**Recommendation:** Consider moving the minting authority to a DAO or a time-locked contract to prevent unilateral supply increases.


### `CP-05` — Centralized Transfer Control  *(Severity: Medium · Status: Unresolved)*

The owner can use lockPool and unlockPool to enable or disable transfers for specific pools. This gives the owner the ability to effectively freeze user assets or halt trading activity.

**Recommendation:** Remove the ability to arbitrarily lock transfers or implement a clear, public-facing policy for when such actions are permitted.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. Of that, 3.8% burned — not holders that can sell, so excluded from the concentration score. What remains: 16.2% in wallets, 80.0% in other contracts. The deployer/owner wallet itself holds 16.2%. 6,141 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

6,141 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $79K (DexScreener, all pools). 24h trading volume $402K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: a ProxyAdmin contract. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $79K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x53cc...ee65`](https://basescan.org/address/0x53cc21bdba3c574e6273569fc2267d17469dee65) |
| **Network** | Base |
| **Price** | $0.04238 |
| **24h Volume** | $401.9K |
| **Liquidity** | $79.4K |
| **Volume / Liquidity** | 5.1× |
| **Token Age** | 11h |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1364 buys / 1314 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ⚠️ Unknown |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/base/0xea47e550604225b25ee8cd25800e2071df08a677ce5dc605028f671eddbe7b71)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/united-dividend-trust-fund-base-1f8d)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-24*
